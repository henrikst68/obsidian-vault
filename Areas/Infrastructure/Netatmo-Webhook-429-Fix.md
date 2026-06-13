# Netatmo Webhook 429 — Permanent Fix (Polling Mode)

Resolved 2026-06-13. The Netatmo integration intermittently dropped all sensors (incl. the rain sensor) to `unavailable`.

## Root cause
On every HA startup/reload the integration called `api.netatmo.com/api/addwebhook`, which Netatmo throttled with `429 – API limit exceeded (26)`. That raised `ConfigEntryNotReady` and dropped the entities. Same issue first diagnosed 2026-06-04; that time it was only waited out.

## Permanent fix applied
Disabled webhooks so the integration uses polling instead of push:
1. Called service `netatmo.unregister_webhook` (detaches current session webhook).
2. Stopped HA (`docker stop homeassistant`).
3. Edited `.storage/core.config_entries` — removed `webhook_id` and `cloudhook_url` from the Netatmo entry's `data` (entry_id `01JFJCRQ3VDD9C8WQSNX0N9293`, title "Home Assistant Cloud"). Backup: `.storage/core.config_entries.bak.1781373794`.
4. Started HA.

**Why this works:** in `netatmo/__init__.py`, `register_webhook()` only registers when `CONF_WEBHOOK_ID` is present in `entry.data` (line ~142). With it removed, `addwebhook` is never called, so the 429 cannot recur. Data still updates via the built-in poll loop — `SCAN_INTERVAL = 60` in `netatmo/data_handler.py` — i.e. every 60 s.

## Verification
- No `addwebhook`/429 lines after restart.
- `sensor.netatmo_rain_sensor_precipitation` reporting live again (0 mm), `_today` 5.2 mm, connectivity on, battery 100%.
- `binary_sensor.automower_rain_imminent` now consuming a real live value.

## Notes / trade-offs
- The entry was set up via **Nabu Casa Cloud**, so webhooks *were* deliverable — the 429 was pure Netatmo API rate-limiting, not reachability.
- Polling at 60 s is more than fine for rain detection (forecast sensor refreshes every 15 min anyway).
- **Caveat:** re-adding the Netatmo integration via the UI will recreate `webhook_id` and reintroduce the 429 on frequent restarts. If that happens, repeat this fix.
- The earlier weakness note in [[Automower-Rain-Control]] (live detection lost during Netatmo dropouts) is now largely moot, since the dropouts were caused by this webhook issue.
