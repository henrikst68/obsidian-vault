---
date: '2026-09-21'
status: partially-resolved
tags:
  - incident
  - home-assistant
  - tailscale
  - dns
---
# Incident: Met.no nowcast unavailable (2026-09-14 → 2026-09-21)

## Symptom
`weather.met_no_nowcast_sandgraven` unavailable from 2026-09-14 20:05 UTC. Core `met` integration also failing (`ClientConnectorDNSError`).

## Root cause
1. Pi Tailscale node key expired 2026-09-14 22:04 CEST ("netmap expiry timer triggered", private key zeroed). tailscaled state: `Needs login`.
2. `homeassistant` container (network_mode: host, started 2026-07-17) had a stale resolv.conf snapshot pointing only at MagicDNS `100.100.100.100` / `fd7a:115c:a1e0::53`.
3. MagicDNS stops answering when Tailscale is logged out → all DNS in HA failed. Host itself resolves fine via Pi-hole (192.168.1.2).
4. Tailscale upgrade 1.102.2 → 1.102.4 at 23:04 CEST was coincidental, not causal.

## Fix applied 2026-09-21 (Pi, /opt/docker/docker-compose.yaml)
- Backup: `docker-compose.yaml.bak-20260921-1818`
- An existing `dns: 192.168.1.2, 1.1.1.1` line (single string, invalid) was corrected to a YAML list:
  ```yaml
  dns:
    - 192.168.1.2
    - 1.1.1.1
  ```
- Verified Docker 28.4.0 accepts `dns` with `network_mode: host`.
- Confirmed running image ID == local `:stable` before recreate (no unplanned upgrade).
- `docker compose up -d --force-recreate homeassistant`
- Verified: container resolv.conf = 192.168.1.2, 1.1.1.1; api.met.no resolves 3/3; nowcast state `sunny` at 16:19 UTC.

## Still open
- Tailscale on Pi still `Needs login` → Funnel down (AITrainingCoach, Craniolog, Supabase public access affected). Requires Henrik: `sudo tailscale up` + disable key expiry for `pi` in Tailscale admin.
- Automower rain-prevention ran on Netatmo only for 7 days. Argues again for fail-safe-wet when a rain signal is unavailable.

## Lesson
HA DNS must not depend on Tailscale. Container DNS is now pinned explicitly.
