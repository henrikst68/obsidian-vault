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

## Verification
All 93 entity references in the rebuilt view resolve (0 missing). 6 cards.

## CORRECTION to [[Automower-Rain-Control]]
That note claimed all `switch.am430x_nera_*` were `unavailable` and the cold automations dead because of a missing switch. As of this session the switches have **recovered** — `switch.am430x_nera_enable_schedule` is live and `on`. The cold automations' broken reference (`5eb2c1f4…`) was a stale unique_id, but the schedule switch itself now works. Revisit reviving the cold automations against `switch.am430x_nera_enable_schedule`.

## Backups
- `.storage/lovelace.lovelace.bak.1781376165`
- `.storage/core.entity_registry.bak.*`
