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
