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
