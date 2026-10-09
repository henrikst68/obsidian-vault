---
date: 2026-10-09T00:00:00.000Z
status: open-diagnosed
tags:
  - incident
  - home-assistant
  - tado
  - matter
---
# Incident: Tado integration down since 2026-09-21, Matter devices dead since Feb 2025

## Symptom
- Tado config entry `Sandkassen` (home id 1761665): `setup_error`, "Device login flow status is PENDING. Starting re-authentication". 95 entities unavailable since 2026-09-21 16:24 UTC.
- 30 `matter` entities (Tado X thermostats/sensors) unavailable.

## Facts (observed)
- Tado went down in the same minute as the `homeassistant` container was force-recreated (2026-09-21 ~18:19 local, see Incident-2026-09-14-HA-DNS-Tailscale).
- Reauth by Henrik on 2026-10-09 22:54 WORKED (new token stored, "Tado connection established"). The first data fetch then fails: `KeyError: 'shortSerialNo'` in `tado/coordinator.py` line 142 (`_update_device_info`). The failed first setup consumes the one-time refresh token, so the retry 5 s later gets HTTP 400 and HA asks for a new login. Every new login repeats this loop.
- Same error pattern is in the log of 2026-09-21 18:19, i.e. the original failure was not an expired token.
- Registered Tado devices before the failure were classic: 8x VA04, 2x SU04, 1x IB02, 7 zones. Config entry created 2026-03-17 (re-added after an earlier Tado problem; `/opt/homeAssistant/startup.sh` dated 2026-03-16 pins python-tado==0.18.16, which equals what HA 2026.3.2 itself requires, so the pin is a no-op today).
- Core HA docs: Tado X devices are not supported by the Tado integration, they must use Matter. Open HA issue with the same symptom: home-assistant/core#157765.
- PyTado uses the X-line API when the home info has `generation == "LINE_X"`; HA 2026.3.2 has no X-line code (reads `shortSerialNo`).

## Not verified
- The actual `generation` value and device list returned by Tado for home 1761665. Hypothesis: Tado now returns an X-line shape for this home. One authenticated read-only call would settle it.
- What changed on the Tado side or in the Tado app around 2026-09-21.

## Matter
- matter-server (7.0.0b0) loads 0 nodes. The 10 Tado X nodes are in `5886038109057362053.json` (last written 2025-02-25) but the server now runs under fabric `15644049753008230766`: the root CA in `chip.json` was replaced after Feb 2025. No copy of the old CA key found on the Pi (checked /opt, /home, /root, /var/backups, both Docker volumes, HA backups not applicable).
- So `climate.*` Matter entities have been dead about 20 months (matches the earlier note "Tado climate.* perpetually unavailable").
- Recommissioning of all 10 devices into the current fabric is the only way back; physical work.

## Other
- Tado debug logging is on in configuration.yaml and prints the refresh token in plain text in the log.

## Open decisions (Henrik)
1. Run one throwaway read-only PyTado login to see `generation` + device shape (needs one device-login approval; does not touch HA's token).
2. Matter: recommission 10 devices vs retire.
3. Do not approve further Tado reauth in HA until the cause is fixed: each attempt fails the same way.

No changes were made on the Pi during this diagnosis.


## Update 2026-10-09 23:3x: read-only check result (separate device login, nothing stored, HA untouched)
- Home 1761665 is the only home on the account (index 0), same id as the HA config entry.
- Tado reports `generation: LINE_X` for the home. PyTado therefore uses the X-line API, which returns devices with `serialNumber` and no `shortSerialNo` -> HA 2026.3.2 core integration fails with KeyError at setup. This is confirmed, not inferred.
- Device list: 10 devices (8x VA04, 2x SU04) + 1 non-dict list entry (shape differs; probably the bridge). VA04/SU04 are the Tado X thermostat/sensor models, i.e. the SAME 10 physical devices as the 10 Matter nodes (8 thermostats + 2 sensors). Earlier assumption that cloud and Matter devices were different hardware was wrong.
- 7 zones returned (keys: roomId, roomName, devices, zoneControllers, ...).
- Henrik does not recall any change on the Tado side. Most likely Tado changed the home/API (generation) or the legacy fields it still served; the already-running HA process kept its old API object until the container was recreated on 2026-09-21, which forced a fresh setup. Exact flip date unknown (between 2026-07-17 and 2026-09-21).
- Consequence: the core Tado integration cannot work for this home until HA adds X-line support. Supported path per HA docs = Matter. Matter needs recommissioning of the 10 devices (old fabric key lost).
- Cleanup: check script and log removed from the Pi, plus my earlier temp copies /tmp/er.json and /tmp/st_m.json.
