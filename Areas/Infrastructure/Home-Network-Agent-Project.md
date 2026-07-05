---
tags:
  - infrastructure
  - vpn
  - wireguard
  - hetzner
  - home-assistant
  - raspberry-pi
  - agents
  - security
status: active
created: '2026-05-31'
updated: '2026-05-31'
---
# Home Network Agent Project

**Status:** Active — created 2026-05-31
**Purpose:** Develop integrations and deploy agents across the home network (Home Assistant, Pi, Hetzner VPS) for expanded capability and hands-on learning.

> Companion to [[TODO-document-wireguard-vpn]]. This note supersedes the connectivity-planning portion of that TODO; the Pi-side WireGuard documentation tasks remain open there until captured directly from the Pi.

## Current topology (verified 2026-05-31)

Three network islands that cannot currently reach each other:

| Island | Details | LAN route? |
|---|---|---|
| Claude sandbox | Package-registry allowlist only; has Hetzner MCP (shell + vault) + Google MCP | No |
| Hetzner VPS | `ubuntu-4gb-nbg1-1`, nbg1, public `178.104.150.20`, root, single `eth0`, **no VPN client installed** | No |
| Home LAN | `192.168.1.0/24`; Pi at `192.168.1.2` (Home Assistant `:8123` in Docker); WireGuard VPN host; Hue, etc. | Reachable only from inside the house |

Verified from the Hetzner shell: no WireGuard/Tailscale binaries, no tunnel interfaces, `ping`/`curl` to `192.168.1.2` time out (RFC1918, no route from datacenter). The Pi is currently the **sole VPN host** per [[TODO-document-wireguard-vpn]].

## Connectivity decision

**Chosen: extend the existing self-hosted WireGuard to the Hetzner VPS as a new peer.**

Rationale — reconsidered after discovering the Pi already runs WireGuard:
- WireGuard has the smallest *trust surface* of the options (no third-party coordination plane; only the two keypairs you generate can authenticate). Audited, in-kernel, silent to unauthenticated scanners.
- A VPN keeps Home Assistant reachable **only from inside an authenticated tunnel** — strictly better than exposing the HA API publicly (Cloudflare Tunnel / Nabu Casa / reverse proxy all publish an attackable auth endpoint).
- You already operate WireGuard, so extending it avoids introducing a second overlay (Tailscale) and its added trust dependency. Reuse beats parallel systems.

Rejected:
- **Tailscale** — strong, easier revocation/identity, but adds a coordination-plane trust dependency and a redundant overlay given existing WG.
- **Expose HA API (CF Tunnel / Nabu Casa / proxy)** — largest exposed surface; makes HA auth remotely attackable. Worst option regardless of method.

### Open sub-task carried from the TODO
Adding the Hetzner peer must be doable **without being on the home LAN**. This is the same need as the TODO's "create new VPN clients from external networks." Resolution approach to evaluate once Pi is reachable: a management path (e.g. `wg-easy`) or a documented manual peer-add procedure run via the Pi MCP tool.

## Security posture

Two concerns dominate the WG-config details:

1. **The Hetzner box would become a public-IP machine holding a route into the home.** Its own hardening matters more than tunnel choice. A compromised endpoint defeats the VPN.
2. **The long-lived HA token grants full API access.** It must not rest in env vars on the public box nor travel through the connectivity layer. Scope per-agent capability; keep the token off the bridge host.

### Hetzner hardening checklist (to apply)
- [ ] SSH: key-only, `PasswordAuthentication no`, root login restricted
- [ ] Firewall (ufw/nftables): default-deny inbound; allow only SSH + WG listen port
- [ ] `unattended-upgrades` for security patches
- [ ] `fail2ban` on SSH
- [ ] WireGuard peer config with tight `AllowedIPs` (only the HA host/subnet actually needed, not `0.0.0.0/0`)

## Agent model: detection vs. action

The governing split for anything running unattended:

- **Autonomous (read-only, reversible, safe):** poll WG/Tailscale peer status for unexpected nodes; watch `journalctl`/auth logs for SSH anomalies; check HA API for failed-auth spikes; verify tunnel health; diff ACL/config against a known-good baseline; **alert via Gmail/notification.**
- **Agent-prepared, human-approved (irreversible):** key rotation and peer/node revocation. The agent identifies the issue, drafts the exact command, explains why — a human authorizes the destructive act. Standing autonomous revocation authority is itself a new attack surface and a self-lockout risk; explicitly **not** built.

Runtime note: unattended monitoring requires a persistent runtime on the Hetzner box (systemd timer / small daemon that escalates to the human). Claude is episodic and acts only when present — it builds and periodically reviews the agent; it is not an always-on sentinel.

## What Claude can/can't provision

- **Can (via Hetzner shell):** all Hetzner-side install, hardening, WG peer config, monitoring scaffolding — delivered as reviewable scripts, not silent execution.
- **Can (if Pi MCP tool connected):** equivalent on the Pi.
- **Cannot by design:** the WireGuard key exchange still requires you to place/approve keys; account auth flows are performed by you, not Claude. The node-join step that mints trust stays human.

## Blockers / pending

- [ ] **Pi not reachable from here** — Pi MCP tool (`mcp__pi-assistant__run_command` per setup) not connected in this environment. Needed to capture WG config and provision Pi side.
- [ ] Pi-side WireGuard facts still undocumented — see [[TODO-document-wireguard-vpn]] checklist (server config, listen port, subnet, DNS, peers, key storage, service management).
- [ ] Confirm router port-forward for WG listen port (needed for Hetzner peer to reach Pi endpoint).

## Next actions

1. (Safe, high-value, no LAN dependency) Harden the Hetzner box + stand up **read-only** monitoring agent.
2. Connect the Pi MCP tool; capture WG config into [[TODO-document-wireguard-vpn]].
3. Add Hetzner as a WG peer with tight `AllowedIPs`; verify it can reach HA over the tunnel only.
4. Define per-agent HA token scoping; keep token off the bridge host.


---

## Hardening applied 2026-07-05 — verified

Hetzner VPS (`178.104.150.20`) hardening completed and externally verified. Scripts live in `/root/harden-step{1,2,3}-*.sh` on the box.

### Step 1 — fail2ban (done)
- Installed; SSH jail at `/etc/fail2ban/jail.d/sshd.local`, `systemd` backend, 4 retries / 10 min → 1h ban, escalating (factor 2, max 1 week).
- **Banned 7 active brute-forcers on startup** — password SSH exposure was live, not theoretical.

### Step 2 — firewall / ufw, Option A (done, externally verified)
- Default-deny inbound, allow outbound. Explicit allows: 22 (SSH), 80 + 443 (Caddy). v4 + v6.
- **3100/3101 now Caddy-only**: dropped at the firewall for external traffic; Caddy still proxies them over localhost via `mcp.magleblik.dk` / `shell.magleblik.dk`.
- Applied behind a 5-min `at` dead-man auto-rollback; cancelled after SSH confirmed working.
- **Verified from an external client (Henrik's PC):** `178.104.150.20:3100` now times out (previously answered instantly). SSH from outside confirmed working. NB: testing port reachability *from the box itself* gave a false 404 — external verification is the trustworthy check.

### Step 3 — SSH key-only (done, verified)
- Drop-in `/etc/ssh/sshd_config.d/99-hardening.conf`: `PasswordAuthentication no`, `KbdInteractiveAuthentication no`, `PubkeyAuthentication yes`, `PermitRootLogin prohibit-password` (reported as `without-password`, functionally identical).
- Guards: `sshd -t` validation + refuses if zero authorized_keys + `reload` not `restart` (sessions survive).
- **Verified:** fresh key login as `adminhenrik` works with passwords disabled.

### Access model now
- `adminhenrik` (uid 1000): key login (ED25519 `SHA256:IAWE2jA+…`, dedicated key generated on Henrik's PC) + **passwordless sudo** via `/etc/sudoers.d/adminhenrik`. Key boundary = possession of the passphrase-protected private key.
- `root`: key-only (ED25519 `SHA256:gANmiM2…`), retained as fallback.
- Revert SSH hardening if ever needed: `rm /etc/ssh/sshd_config.d/99-hardening.conf && systemctl reload ssh`.

### Checklist status (from project note)
- [x] SSH key-only, password auth disabled, root restricted
- [x] Firewall default-deny; only SSH + Caddy (WG port still to add later)
- [x] unattended-upgrades (was already installed)
- [x] fail2ban on SSH
- [ ] WireGuard peer with tight `AllowedIPs` — pending Pi reachability

### Still open / next
- Read-only monitoring agent (the other half of the "safe, no-LAN-dependency" work) — not yet built.
- Everything Pi-side (WG config capture, Hetzner-as-peer) — still blocked on Pi MCP connectivity.
- Optional later: rebind node services to `127.0.0.1` (Option B) as defence-in-depth beyond the firewall.
