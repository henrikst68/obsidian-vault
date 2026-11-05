---
date: '2026-11-04'
tags:
  - infrastructure
  - security
type: security-check
---
# Security check — 2026-11-04 22:00

Run by Claude from claude.ai via `pi.magleblik.dk:run_command`. Hetzner verified from outside only (no hetzner-shell from claude.ai). Home WAN exposure could not be tested from outside (router hairpin only, inconclusive).

## Standing rules — hold
- Hetzner public (178.104.150.20) TCP scan from home WAN: only 22, 80, 443 open. 3100 and 3101 closed.
- Hetzner SSH: root and henrik both `publickey` only (no password offered).
- Hetzner :80 → 308 redirect to HTTPS.
- `mcp.magleblik.dk` and `pi.magleblik.dk`: 401 without auth on `/` and `/mcp` (POST tools/list).
- TLS: mcp.magleblik.dk to 2027-01-09, pi.magleblik.dk to 2026-12-08, pi.tail63e8cd.ts.net to 2026-12-11 (auto-renew expected).

## Finding 1 (HIGH) — Pi MCP shell unauthenticated on all interfaces
- `/home/piadmin/mcp_server.py` (`mcp-server.service`) binds `0.0.0.0:8765`, no auth in code, DNS-rebinding protection disabled. Auth exists only at the Hetzner Caddy front end.
- Confirmed live: unauthenticated MCP `initialize` to `http://192.168.1.2:8765/mcp` → HTTP 200 + session id.
- Server runs as `piadmin`, which has `(ALL) NOPASSWD: ALL`. Effect: any device on the home LAN or any WireGuard peer (incl. family devices) can get root on the Pi.
- Note: probing the server from its own run_command deadlocks (synchronous subprocess blocks the event loop); probe had to run detached.
- Fix options (pending approval): (a) nftables rule on Pi: allow tcp/8765 only from 10.241.173.6 and 127.0.0.1, drop rest; (b) bind to 10.241.173.1 + bearer token check in the app; (c) restrict piadmin sudo. Confirm Hetzner Caddy upstream address before (a)/(b) to avoid cutting the connector.

## Finding 2 (MEDIUM) — Supabase public signup open via Tailscale Funnel
- Funnel exposes Caddy :8080 → Craniolog and `/supabase/*` (Kong).
- Without API key: rest/auth/pg all 401. With the public anon key (in Craniolog client bundle): `disable_signup=false`, `mailer_autoconfirm=true` → anyone on the internet can create a confirmed account.
- Mitigation in place: RLS enabled with policies on all public tables (entries 4, profiles 4, user_settings 3). Only 1 auth user exists (created 2026-03-19) → no abuse so far.
- Fix: set `GOTRUE_DISABLE_SIGNUP=true` (single-user app).

## Finding 3 (LOW/MEDIUM) — Pi host hardening
- No host firewall: INPUT policy ACCEPT (only Tailscale chain).
- Pi sshd: `PasswordAuthentication yes`, `PermitRootLogin without-password`. No failed SSH attempts in 7 days; only accepted logins from 192.168.1.57.
- 93 pending package upgrades incl. openssl, libc6, docker-ce, containerd.io.

## Resolved / clarified
- WireGuard peers identified from wg0.conf comments: .2 HenrikMobil, .4 DortheMobil, .5 DortheIpad. Their endpoint shows 192.168.1.1 (router NAT), so real source IPs are not visible on the Pi.
- Yoga .8 last handshake ~38 days ago; .7 S24 and .9 Asus still never.
- GitHub runner: container and `/opt/apps/github-runner` removed since 2026-10-04; no PAT strings found under /opt/apps.
- Mosquitto: `allow_anonymous false` with password file.
- filament-manager (:8770, new since last check): LAN/WG only, serves UI without auth.


## 2026-11-05 07:10 — Finding 1 fixed (nftables guard)
- Pre-check: only established peer on :8765 was 10.241.173.6 (Hetzner Caddy upstream).
- Rule file: `/etc/nftables.d/mcp-guard.nft`, separate table `inet mcp_guard` (input hook, priority -10, policy accept): tcp/8765 accept from `lo` and `10.241.173.6`, else counter drop. Does not touch Docker/Tailscale iptables-nft tables.
- Applied with a 5-min auto-rollback timer (`mcp-guard-rollback`); connector verified working, timer cancelled.
- Persistence: `mcp-guard.service` (oneshot, enabled, ordered before network-pre and mcp-server.service). `systemctl stop mcp-guard` removes the table.
- Verification: probe from craniolog container (172.19.0.2, bridge) → blocked, drop counter 4 packets. Self-probes from the Pi to 192.168.1.2/10.241.173.1 go via `lo` and are allowed by design — not a valid test.
- Not yet tested from a physical LAN device or a family WG peer; expected to be dropped (non-lo, saddr not .6).
- Residual: `piadmin` still has NOPASSWD sudo and the app still has no auth — security now depends on Hetzner Caddy auth + this rule. Rollback: `sudo systemctl disable --now mcp-guard`.
