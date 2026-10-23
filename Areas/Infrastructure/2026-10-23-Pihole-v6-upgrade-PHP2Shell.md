---
date: '2026-10-23'
tags:
  - infrastructure
  - pi
  - pihole
  - security
  - cve
---
# Pi-hole v5 → v6 upgrade (PHP2Shell remediation) — 2026-10-23

## Why
CVE-2026-109618 / CVE-2026-109619 (PHP core RCE, CVSS v4 9.2, disclosed 2026-10-20/21). Fixed only in PHP 8.2.35 / 8.3.36 / 8.4.27 / 8.5.12.
Audit of the Pi found exactly one PHP instance: the `pihole` container (image pulled 2024-07, Pi-hole v5.18.3) running **PHP 7.4.33 php-cgi** behind lighttpd on `0.0.0.0:80` (host networking). No upstream fix for 7.4 in that image.
Not affected: host OS (no PHP packages), Home Assistant, AITrainingCoach, Craniolog, Caddy, Supabase stack. Hetzner shows `server: Caddy`, no PHP indicators — not verified with dpkg (hetzner-shell not reachable from claude.ai).
Pi-hole admin UI was not behind the Tailscale Funnel (Funnel → 127.0.0.1:8080 Caddy only).

## What was done (Pi, as piadmin)
- Compose: `/opt/docker/docker-compose.yaml`; backup `docker-compose.yaml.bak-20261023-0836`
- Config backup (container stopped, excludes 1.4 GB `pihole-FTL.db` query log): `/opt/pihole-v5-config-20261023.tgz`
- Rollback image tagged: `pihole/pihole:v5-rollback` (78de8a1eefcf)
- Env rename: `WEBPASSWORD` → `FTLCONF_webserver_api_password`
- Pulled `pihole/pihole:latest` (2026.10.0) → Core v6.5 / Web v6.6.1 / FTL v6.8; `docker compose up -d pihole`

## Verified after
- Container healthy; DNS resolves on 192.168.1.2; blocking works (doubleclick.net → 0.0.0.0)
- v5 setupVars.conf auto-migrated to pihole.toml; gravity 73,634 domains, 1 adlist; 3/3 local DNS records migrated (custom.list → dns.hosts; original in `migration_backup_v6/`)
- listeningMode ALL, upstreams 8.8.8.8 / 8.8.4.4 (unchanged)
- No PHP or lighttpd in container or on host; port 80 now served by pihole-FTL
- One-off migration-time log error `gravityDB_count ... antigravity_count` — not recurring

## Open items
- Rotate Pi-hole web password (exposed in Claude tool output during the session)
- Optional: add `cap_add: SYS_NICE, SYS_TIME` to silence FTL capability warnings (cosmetic; NTP client disabled is fine since host does NTP)
- Optional: restrict FTL webserver to LAN/WG (`FTLCONF_webserver_port`) instead of all interfaces
- Rollback: `docker compose stop pihole`, restore tgz to /opt, restore compose backup, set image `pihole/pihole:v5-rollback`, up -d
- Confirm no router port-forward to 192.168.1.2:80 (WAN probe from LAN inconclusive due to hairpin)
