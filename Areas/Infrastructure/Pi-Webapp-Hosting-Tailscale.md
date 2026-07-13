---
created: '2026-07-13'
status: active
tags:
  - infrastructure
  - tailscale
  - caddy
  - raspberry-pi
  - docker
  - retroactive-documentation
updated: '2026-07-13'
---

# Pi Webapp Hosting — Tailscale Funnel + Caddy

**Status:** Active, in production use. **Documented retroactively 2026-07-13** during an infrastructure audit — this stack was built by Claude before the Obsidian vault was adopted for project documentation, so it was never written up. It predates [[Home-Network-Agent-Project]] (Caddy container created 2026-03-18; the agent project started 2026-05-31) and is a separate concern from it.

## Purpose

Public hosting for personal app projects on the Pi, unrelated to Home Assistant / the MCP agent work.

## Architecture

```
Internet → Tailscale Funnel (https://pi.tail63e8cd.ts.net)
         → 127.0.0.1:8080 (local Caddy, container "caddy")
         → routed by path to:
             /supabase/*        → supabase-kong:8000
             /api/*, /webhook/*  → AITrainingCoach:4000
             /training*          → AITrainingCoach:4000
             /* (catch-all)      → craniolog:3000
```

- **Tailscale**: installed on the Pi, tailnet `tail63e8cd.ts.net`. Funnel enabled, proxying the single hostname `pi.tail63e8cd.ts.net` to local port 8080. This is Tailscale's own public-ingress feature — traffic reaches the Pi without going through Hetzner.
- **Caddy** (`/opt/caddy/Caddyfile`, container `caddy`): reverse proxy on `:8080`, `auto_https off` (TLS is terminated by Tailscale Funnel, not Caddy). Also serves `/health`.
- **Apps behind it:**
  - **Supabase** (`/opt/apps/supabase/docker-compose.yml`) — kong, auth, rest, meta, postgres db
  - **AITrainingCoach** (`/opt/apps/AITrainingCoach/docker-compose.yml`) — API + webhook + frontend at `/training`; has a paired `github-runner-aitrainingcoach` container for CI
  - **Craniolog** — catch-all app on port 3000

## Security posture — as found, not yet reviewed

- This is a **second independent public ingress path** into the Pi, separate from the Hetzner-only-ingress model documented for the MCP/Home Assistant side in [[Home-Network-Agent-Project]]. Traffic here bypasses Hetzner's fail2ban/ufw hardening entirely — it rides on Tailscale's infrastructure instead.
- The Pi itself has **no local firewall** (`ufw` not installed). Everything bound to `0.0.0.0` (SSH, FTP, MQTT, Home Assistant, the Pi MCP server, Supabase Kong, this Caddy) is reachable from the LAN and from the Tailscale mesh regardless of what Funnel exposes. Funnel only controls what's reachable from the *public internet*; it doesn't add any containment on the Pi side.
- Not yet assessed: whether Supabase/AITrainingCoach/Craniolog have their own auth in front of them, or rely solely on obscurity of the URL paths.

## Open questions / next steps

- [ ] Decide if this stack should stay on Tailscale Funnel or move behind Hetzner ingress for consistency with the rest of the security model
- [ ] Add a local firewall on the Pi (tracked in [[Home-Network-Agent-Project]])
- [ ] Confirm auth posture of each app behind Caddy
