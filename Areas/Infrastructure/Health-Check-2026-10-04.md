---
date: '2026-10-04'
tags:
  - infrastructure
  - health-check
type: health-check
---
# Health check — 2026-10-04 08:41

Run by Claude from claude.ai via `pi.magleblik.dk:run_command` (Pi) and `Hetzner MCP` (vault). Hetzner systemd units were NOT inspected directly (no hetzner-shell from claude.ai; `piadmin` key not on Hetzner). Hetzner is verified from outside only.

## Healthy
- Pi: uptime ~12 weeks, disk 20%, RAM 3.0/4.0 GiB, 63 °C, no failed systemd units.
- Docker: 13/14 containers up (homeassistant, pihole, caddy, AITrainingCoach, craniolog, supabase-*, postgres, mosquitto, matter-server).
- Local HTTP: HA :8123 → 200, app :8080 → 200, Pi-hole /admin → 302. Pi-hole resolves.
- Public: Tailscale Funnel `pi.tail63e8cd.ts.net` → 200. `mcp.magleblik.dk` and `pi.magleblik.dk` → 401 at root (expected, auth required). Both connectors functional in session.
- Hetzner over WG (10.241.173.6): handshake 110 s, TCP 22/443/3100/3101 open; shell-mcp answers MCP `initialize` (mcp-server-commands 0.8.2).
- Hetzner public (178.104.150.20), tested from home WAN: 443 open, 3100 and 3101 closed. Security rule for 3101 holds.
- Vault: 104 notes; last GitHub commit 2026-10-02 07:10Z matches last vault write → auto-sync current.
- WAN IP unchanged: 90.185.97.137.
- Rain signals reporting: nowcast, Netatmo rain sensor (connected, battery 94%), `binary_sensor.automower_rain_imminent`.

## Fault: github-runner-aitrainingcoach restart loop
- Symptom: container `Restarting`, RestartCount 26,925. Logs: "already configured" + runner removal fails with HTTP 401.
- Root cause (confirmed): the classic PAT (`ghp_…`) in `/opt/apps/github-runner/.env` (`RUNNER_TOKEN`, mapped to `ACCESS_TOKEN` in docker-compose.yml) is rejected by the GitHub API — `/user` returned 401 three times out of three, `/repos/.../actions/runners` 401. Token expired or revoked.
- First 401 in retained logs: 2026-09-14 22:24Z → AITrainingCoach CI has not run since at least that date.
- "Already configured" is a secondary symptom: the restarted container keeps its old runner config in its filesystem. A `--force-recreate` clears it.
- Action taken 08:47: `docker stop github-runner-aitrainingcoach` to stop the loop (reversible; restart policy `unless-stopped` keeps it stopped).
- Side finding: `.env` is mode 644 (world-readable) and contains the PAT. Should be 600.

### Fix (pending Henrik)
1. Create new token. Fine-grained PAT: repository `henrikst68/AITrainingCoach` only, permission Administration: Read and write (+ Metadata: Read). Or classic PAT with `repo` scope. Set an expiry and note it here.
2. Replace `RUNNER_TOKEN` value in `/opt/apps/github-runner/.env`; `chmod 600 .env`.
3. `cd /opt/apps/github-runner && sudo docker compose up -d --force-recreate`.
4. If registration fails on name clash, remove the offline `pi-arm64` runner in repo Settings → Actions → Runners, then recreate again.
5. Verify runner shows Idle in GitHub.

## Other findings
- HA Xbox integration: 1,068 of ~1,090 HA errors in last 24 h. Disable or reauthenticate.
- HA `husqvarna_automower_ble`: "mower does not appear to be pairable" (13/24 h). `sensor.am430x_nera_next_start`, charging sensors unavailable. Cloud `husqvarna_automower` only 1 error. Confirm which integration the rain package depends on.
- Unavailable entities (9): two TVs, outdoor camera + light, ZAP charger controls, Automower BLE sensors — likely powered off/asleep except Automower.
- WireGuard peers: Yoga .8 last handshake ~6.5 days (known: no auto-start); Asus .9 and S24 .7 never (known). Undocumented peers: .2 (last ~45 days), .4 (active, 276 s), .5 (~6.8 days) — need identification.
