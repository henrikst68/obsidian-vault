# Steffen Tab — AM430X NERA Dashboard Rebuild

Rebuilt 2026-06-13. The Lovelace "Steffen" view (`path: steffen`) was rebuilt against the current Husqvarna Automower integration.

## Integration version
- Built-in core integration `husqvarna_automower` (codeowner @Thomas55555), NOT a HACS custom component.
- Ships with HA core **2026.3.2**, lib `aioautomower==2.7.3`. "Updating the integration" = updating HA core (container image pull) — not done here, no in-HA update entity exposed.

## Deprecated entity removed
- `binary_sensor.am430x_nera_returning_to_dock` — **deprecated/removed** from the integration. Current `binary_sensor.py` only defines `battery_charging` and `leaving_dock`; `returning` is not found anywhere in the source. It was a permanently-`unavailable` orphan. Removed from the dashboard AND deleted from `.storage/core.entity_registry` (HA stopped → edit → start). Registry backup: `core.entity_registry.bak.*`.

## Kept (not deprecated, just situationally unavailable)
- `sensor.am430x_nera_next_start` — valid timestamp sensor (`next_start_timestamp`); shows `unavailable` only while actively mowing (no scheduled next start). Populates when docked.

## New entities added to the tab
Integration now exposes far more than the old dashboard had. Added:
- **Mower control card** (`tile` + `lawn-mower-commands`: start/pause + dock) for `lawn_mower.am430x_nera`.
- **Status:** work_area (current), inactive_reason, remaining_charging_time (new).
- **Styring:** `switch.am430x_nera_enable_schedule`, `select.am430x_nera_headlight_mode`, buttons `sync_clock` / `confirm_error` / `reset_cutting_blade_usage_time`.
- **Arbejdsområder (compact):** per-area enable switch + progress sensor for 11 work areas.
- **Klippeplan:** `calendar.am430x_nera` (listWeek).

## 11 work areas
primaer_have, drivhus, hus_nord, hus_syd, skarp_stigning_hus_vest, langs_sandgraven, hojbede, skur, sti_ost, haengepil_sti, 2_aebletraeer.
Note: **langs_sandgraven has no `_progress` sensor** (only switch + cutting_height), so its progress row was omitted to avoid a broken reference. Each area also has `number.*_cutting_height`; some have `*_last_time_completed`.

## Disabled-by-integration entities (left disabled, available if wanted)
`number.am430x_nera_cutting_height`, `sensor.am430x_nera_downtime`, `sensor.am430x_nera_uptime`.

## Live position map (added later same day)
Added a **core `map` card** ("Position", inserted as card #2, right after the control tile) using `device_tracker.am430x_nera`. Config: `hours_to_show: 2` (trail covering a mow session), `default_zoom: 19`, `theme_mode: auto`.

**GPS cadence (measured from history):**
- Mowing → coords update every **~20–30 s**, real movement, metre-scale steps.
- Docked/idle → reported ~every 60 s but fixed at the dock (≈56.06375, 12.14001).
- `source_type: gps`; real accuracy ≈1–3 m → marker jitters slightly even when moving.

The integration's `device_tracker` only exposes `positions[0]` (latest point), not the full track. A breadcrumb/track would need the `positions` array (API/diagnostics only) or recorder history + a path-drawing card.

**Map options considered (went with option 1):**
1. Core `map` card — done. Generic OSM tiles (no view of actual lawn/beds).
2. `custom:map-card` (HACS) with satellite/WMS tiles — e.g. DK orthophoto (Kortforsyningen/Datafordeler) to see the real garden. Best "useful live map" upgrade if OSM too abstract.
3. `picture-elements` over a garden orthophoto/Husqvarna-app screenshot, mower icon via lat/lon→x/y template (2-corner calibration). Nicest, app-like.
4. Position history/trail — recorder + path card, or pull `positions` array.

## Verification
All entity references in the rebuilt view resolve (0 missing). 7 cards (after map added).

## CORRECTION to [[Automower-Rain-Control]]
That note claimed all `switch.am430x_nera_*` were `unavailable` and the cold automations dead because of a missing switch. As of this session the switches have **recovered** — `switch.am430x_nera_enable_schedule` is live and `on`. The cold automations' broken reference (`5eb2c1f4…`) was a stale unique_id, but the schedule switch itself now works. Revisit reviving the cold automations against `switch.am430x_nera_enable_schedule`.

## Backups
- `.storage/lovelace.lovelace.bak.1781376165`
- `.storage/core.entity_registry.bak.*`
