---
tags:
  - infrastructure
  - vpn
  - wireguard
  - todo
  - raspberry-pi
status: open
created: '2026-05-31'
---
# TODO: Document WireGuard VPN on Raspberry Pi

**Status:** Open — created 2026-05-31

## Context
WireGuard VPN is running on the Raspberry Pi but is **not currently documented** anywhere in the vault. Discovered this gap on 2026-05-31 when looking for the config. The Hetzner VPS (`ubuntu-4gb-nbg1-1`, nbg1) has no VPN — only `eth0`, no WireGuard, no Tailscale — so the Pi is the sole VPN host.

## To document at first opportunity
- [ ] Server config: `/etc/wireguard/*.conf` (interface name, e.g. `wg0`)
- [ ] Listen port + how it's exposed (router port-forward? which WAN port?)
- [ ] VPN subnet / address range used for the tunnel
- [ ] DNS pushed to clients (Pi-hole at `10.x`?)
- [ ] AllowedIPs strategy (full tunnel vs split tunnel)
- [ ] Existing peers (name, pubkey, assigned IP) — **redact private keys**
- [ ] How the WireGuard service is managed (`wg-quick@wg0`, systemd enabled?)
- [ ] Key storage location and backup
- [ ] Whether `wg-easy` or another management UI is installed

## Open task: create new VPN clients from external networks
Need a way to add peers **without being on the home LAN / SSH'd into the Pi locally**. Options to evaluate — see companion note.


---

## Update 2026-05-31 — linked to project note

Connectivity planning is now resolved in [[Home-Network-Agent-Project]]: the Hetzner VPS will be added as a **new WireGuard peer** to this existing Pi-hosted VPN (chosen over Tailscale and over exposing the HA API). The "create new VPN clients from external networks" task above is the mechanism needed to add that Hetzner peer without being on the LAN — same problem, tracked in both places.

**Still open here (Pi-side capture — Claude cannot reach the Pi yet):** the entire config checklist above. To be filled once the Pi MCP tool is connected.

---

## Update 2026-07-07 — confirmed still not implemented

Verified from Hetzner side: `wg` command not installed, no WireGuard interface present (only `eth0`). Attempted curl from Hetzner to Pi HA (`192.168.1.2:8123`) timed out as expected — no tunnel exists.

Despite the plan being agreed in [[Home-Network-Agent-Project]] (Hetzner as new peer on the Pi's WireGuard VPN), this was never executed. **Action needed:** actually add Hetzner as a peer so Claude/Hetzner-side tools can reach the Pi/HA — not just re-plan it again.

---

## Update 2026-07-07 — Hetzner WireGuard peer deployed and verified

Hetzner is now a live peer on the Pi's WireGuard VPN (`10.241.173.6/24`, split-tunnel: `10.241.173.0/24, 192.168.1.0/24`). Deployed by Henrik on both ends per plan above; Claude generated keys/PSK and verified connectivity from the Hetzner shell.

**Verified 2026-07-07:**
- Handshake established (confirmed via `wg show` on both sides)
- Ping to Pi tunnel IP (10.241.173.1): 0% loss
- Ping to Pi LAN IP (192.168.1.2): 0% loss
- HTTP to Home Assistant (192.168.1.2:8123): 200 OK

**Result:** Claude can now reach Home Assistant directly from the Hetzner shell tool. The original blocker (Claude couldn't reach the Pi/HA except via the laptop-only pi-assistant tool) is resolved.

**Still open (lower priority, from original checklist):** full WireGuard config documentation (peer list, key storage/backup policy, wg-easy or management UI decision) — not blocking, can be done at leisure.
