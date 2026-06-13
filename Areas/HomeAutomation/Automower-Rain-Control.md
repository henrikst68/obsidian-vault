# Automower Rain Control (Home Assistant)

Created 2026-06-13. Docks `lawn_mower.am430x_nera` when rain is imminent or falling, and resumes only if the rain logic was what docked it.

## Where it lives
- HA config package: `/opt/homeAssistant/data/packages/automower_rain.yaml`
- Enabled via `configuration.yaml`:
  ```yaml
  homeassistant:
    packages: !include_dir_named packages
  ```
- Backup of original config: `configuration.yaml.bak.<timestamp>`

## Entities created
| Entity | Purpose |
|---|---|
| `sensor.automower_forecast_2h` | Trigger-template sensor; re-pulls `weather.get_forecasts` (hourly) every 15 min. Attrs: `wet` (bool), `max_probability`. |
| `binary_sensor.automower_rain_imminent` | `on` if live Netatmo rain > 0.1 mm **or** forecast `wet`. Availability tied to the forecast sensor, not Netatmo. |
| `input_boolean.automower_docked_by_rain` | Flag: rain automation owns the current dock. |
| `input_number.automower_rain_resume_delay` | Dry-out delay before resuming (default 45 min). |

## Decision logic
- **Imminent / wet** = next 2 forecast hours have precip ≥ 0.3 mm **or** probability ≥ 60%.
- **Raining now** = Netatmo live precip > 0.1 mm.
- **Dock automation** fires only when mower state is `mowing`.
- **Resume automation** fires only if `automower_docked_by_rain` is on AND mower is `docked`, waits the dry-out delay, re-checks dry, then `start_mowing`. This prevents overriding schedule, cold logic, or night-time docking.

## Why it uses `lawn_mower.*` and not the schedule switch
The old `Automower too cold` / `not too cold` automations target switch unique_id `5eb2c1f453107848569f27bbadfbcfae`, which **no longer exists** in the entity registry (all `switch.am430x_nera_*` are `unavailable`). Those two automations are therefore currently dead/disabled (confirmed via `check_config`). The only live control surface is `lawn_mower.am430x_nera` (services: `start_mowing`, `pause`, `dock`).

## Netatmo dependency / known weakness
Netatmo rain sensor drops to `unavailable` intermittently (the 429 webhook rate-limit issue). The binary sensor is built so a missing live reading is treated as 0 mm and availability follows the forecast sensor instead — so forecast-driven docking still works when Netatmo is down. Live "rain has started" detection is lost during those dropouts.

## Netatmo latency is unfixable — nowcast added instead (2026-06-13)
**Root cause of Netatmo rain delay:** The Netatmo Smart Home Weather Station reports to Netatmo's cloud only every ~10 min (observed 12-min cadence in HA history). Webhooks explicitly do NOT push weather-station data (per official HA Netatmo docs — weather station, air-quality monitor, and public stations are excluded from webhook events). So neither faster polling nor re-enabling webhooks can reduce the live rain delay. It is a hardware/cloud limitation. HA polls WEATHER every ~5 min (`WEATHER: 600 / CLOUD_FACTOR 2` in `netatmo/data_handler.py`) which is already faster than Netatmo's publish, so HA is not the bottleneck.

**Fix: Met.no Nowcast (predictive early warning).** Installed HACS custom integration `toringer/home-assistant-metnowcast` v2.3.6 → `custom_components/metnowcast/`. No pip deps (calls Met.no nowcast HTTP API). Loads cleanly (standard "untested custom integration" warning only). Polls every 7 min but each poll returns the next **90 min** of minute-resolution precipitation — so it predicts rain ahead regardless of poll cadence. Nordic-area only (we qualify).

**Entity contract** (friendly name e.g. `Sandgraven` → `weather.met_no_nowcast_sandgraven`):
- state = condition (`rainy`/`pouring`/`lightning-rainy`/…)
- attr `has_precipitation` (bool) — cleanest trigger
- attr `forecast` / `forecast_json` — 90-min minute array
- attr `radar_online`, `radar_coverage` — guard on radar availability

**ACTION REQUIRED (Henrik, UI step):** Settings → Devices & Services → Add Integration → "Met.no Nowcast" → Name `Sandgraven`, lat `56.0637`, lon `12.1400`. (Name `debug` gives random test rain.) Config-flow can't be safely scripted into .storage, so this is manual.

**Planned wiring (one-step once entity exists):** add nowcast as the fastest of three OR'd signals in `binary_sensor.automower_rain_imminent`:
1. Met.no nowcast `has_precipitation` / precip in next ~15–30 min → predictive, fastest.
2. Met.no hourly forecast `wet` (existing `sensor.automower_forecast_2h`).
3. Netatmo live gauge > 0.1 mm → ground-truth confirmation (slow, kept as backstop).
Guard nowcast term on `radar_online == true`.

### ✅ DONE (2026-06-13) — nowcast wired in
- Henrik created the instance via UI → entity `weather.met_no_nowcast_sandgraven` (lat 56.0637, lon 12.14). Live, radar_online=true, radar_coverage=ok.
- `binary_sensor.automower_rain_imminent` state template now ORs three signals, nowcast first:
  1. **nowcast_wet** = `radar_online==true` AND (`has_precipitation==true` OR state in rainy/pouring/lightning-rainy/snowy-rainy)
  2. **forecast_wet** = `sensor.automower_forecast_2h` attr `wet`
  3. **raining_now** = Netatmo live > 0.1 mm
- Verified live: with nowcast=`rainy`, forecast `wet=False`, Netatmo=0.096 mm (below threshold), the sensor correctly read `on` — i.e. the nowcast alone was driving early detection, exactly the goal.
- Package backup: `packages/automower_rain.yaml.bak.*`.
- Automation entity-ids (from aliases): `automation.automower_dock_when_rain_imminent`, `automation.automower_resume_after_rain` (both `on`).
- Note: `forecast` array is empty in the state attributes; the 5-min-resolution forecast (23 pts) is available via the `weather.get_forecasts` service / `forecast_json` attr if finer triggering is wanted later. Current logic uses `has_precipitation`+state, which is always present.

## TODO / open items
- [ ] Fix or revive the cold-temperature automations (broken switch reference) and make sure cold-dock and rain-resume don't fight (resume re-checks dry but not temp).
- [ ] Consider adding a temp condition to the resume action.
- [ ] Tune thresholds (0.3 mm / 60% / 0.1 mm / 45 min) after observing real behaviour this season.
- [ ] Optional: expose the four entities on the dashboard.

## Maintenance
Edit the package file (needs `sudo`), then `docker restart homeassistant`. Validate first with:
```
docker exec homeassistant python3 -m homeassistant --script check_config --config /config
```
