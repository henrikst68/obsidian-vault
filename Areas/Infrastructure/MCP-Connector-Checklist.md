---
created: '2026-07-07'
status: active
tags:
  - infrastructure
  - mcp
  - connectors
  - claude
updated: '2026-07-07'
---
# MCP Connector Checklist

**Purpose:** Avoid repeat confusion where a Claude surface (Cowork, Claude Code, etc.) reports missing capability that actually exists elsewhere in the account — just not enabled for that session. See the "MCP access scope clarification" section in [[Home-Network-Agent-Project]] for the incident that prompted this.

## Why this happens

Adding a connector via Settings → Connectors makes it exist at the **account** level, and that backend is shared across claude.ai, Cowork, Claude Desktop, and mobile. But:

1. **Per-conversation/session toggle.** Each connector still needs to be individually enabled per session via the "+" → Connectors picker. Existing in the account ≠ enabled in this chat.
2. **Claude Code is a separate mechanism entirely.** It doesn't use the Connectors UI — servers are added via CLI (`claude mcp add ...`) or project/user config. Adding a connector in claude.ai settings does nothing for Claude Code; it must be added there independently.
3. **Local MCP servers (Claude Desktop's `claude_desktop_config.json`)** are yet another separate mechanism — not available in Cowork or claude.ai, and not the same as remote/custom connectors.

## Account-level connectors (as of 2026-07-07)

| Connector | What it is | Notes |
|---|---|---|
| Hetzner (vault) | Obsidian REST API — `mcp.magleblik.dk` :3100 | Storage only: read/write notes, list, tags, frontmatter. No shell, no git. |
| Hetzner Shell | Root shell on VPS — `shell.magleblik.dk` :3101 | Full OS access via `run_process`. No built-in confirmation gate — commands execute immediately as root. |
| Google Drive / Gmail / Google Calendar | Google Workspace | — |
| Draw.io | Diagramming | — |
| pi-assistant | Raspberry Pi shell (`run_command`) | **Not reliably connected** — separate ongoing blocker, see [[Home-Network-Agent-Project]]. Also note: even if connected, Claude's sandbox cannot route to `192.168.1.2` directly (RFC1918 egress block) regardless of this connector's state. |

## Per-surface check (manual — Claude can't verify these remotely)

For each surface actually in use, confirm the relevant connectors are toggled on in that surface's own picker:

- [ ] claude.ai (web/mobile)
- [ ] Cowork
- [ ] Claude Desktop
- [ ] Claude Code — check separately via `claude mcp list`; add missing servers with `claude mcp add --transport http <name> <url>`

## Rule of thumb going forward

When a new connector is added to the account, add it to every surface's picker in the same sitting rather than assuming it propagates. If a Claude session reports "I don't have access to X," treat that as **session-scoped**, not account-scoped, until checked here.


---

## Update 2026-07-13

The `pi-assistant` row above is stale. Verified this session:

| Connector | What it is | Notes |
|---|---|---|
| pi.magleblik.dk | Raspberry Pi MCP (`run_command`) | **Connected and working.** Backed by `mcp-server.service` on the Pi, port 8765. Confirmed via `whoami`/`hostname` returning real Pi values (`piadmin@pi`, `192.168.1.2`). The earlier RFC1918-egress-block caveat no longer applies to this connector specifically, since it's reached via its own public hostname/token, not a direct sandbox-to-LAN route. |

Note the `Hetzner Shell` connector (`shell.magleblik.dk` :3101) was **not** in the active connector list for this session — only the vault connector (`Hetzner MCP`, notes-only) was available. Don't assume Shell access is present without checking the session's tool list first.


---

## Incident 2026-07-13 — connectors pointed to localhost

**Symptom:** Both the Hetzner MCP (vault, `mcp.magleblik.dk`) and `pi.magleblik.dk` connectors stopped working. In-session testing showed partial/intermittent failures rather than a clean refuse — `get_vault_stats` and `get_frontmatter` succeeded while `read_note`/`list_directory` errored, then succeeded on retry — consistent with requests intermittently landing on the wrong target.

**Cause:** Both the Hetzner and Pi MCP connectors were pointed to `localhost` (exact layer — Caddy `reverse_proxy` target vs. the connector URL definition itself — not confirmed; note here if it becomes clear later).

**Fix:** Henrik repointed both connectors; confirmed working again same session (clean `list_directory`/`read_note` calls with no errors after the fix).

**Takeaway:** If a connector shows intermittent rather than total failure (some tool calls succeed, others error and then succeed on retry), that's a signal worth checking the proxy/connector target itself, not just auth or session-scope (see main checklist above).


---

## Decision 2026-07-13 — Hetzner Shell stays WireGuard/LAN-only, will not be re-exposed publicly

**Context:** Henrik attempted to connect the claude.ai connector to `https://shell.magleblik.dk:3101` and it timed out. Root cause: the 2026-07-06/09 Hetzner `ufw` hardening default-denies everything except 22/80/443 — port 3101 is intentionally sealed from direct public access. This is consistent with, and reaffirms, the 2026-07-12 restore-access decision to leave shell-mcp off the public internet (unlike the vault and Pi connectors, which were migrated to the Caddy secret-path token pattern on 443).

**Decision (confirmed by Henrik 2026-07-13):** Hetzner Shell will **not** be given a public Caddy front door, even behind a secret-path token. It remains reachable only from within the WireGuard/LAN mesh — i.e. from Henrik's own connected devices, not from claude.ai (which always connects from Anthropic's infrastructure and can never be a WireGuard peer).

**Practical implication:** claude.ai sessions cannot use Hetzner Shell directly, full stop. For root-level Hetzner OS work initiated from a claude.ai chat, two fallback options exist:
1. Route through the Pi (`pi.magleblik.dk:run_command`) and SSH from Pi → Hetzner over the existing WireGuard tunnel (Hetzner's WireGuard IP: `10.241.173.6`).
2. Do that class of work from a surface that sits inside the network already (Claude Desktop/Code on a WireGuard/Tailscale-connected machine).

**Tested 2026-07-13:** Option 1's network path is real — `ssh 10.241.173.6` from the Pi reaches Hetzner's SSH port cleanly over WireGuard (got to publickey auth), but auth fails: the Pi's `piadmin` key (`~/.ssh/id_ed25519` on the Pi) is not in `authorized_keys` for any account on the Hetzner box. So the fallback path is viable but not yet wired up — would require deliberately adding the Pi's public key to a Hetzner account's `authorized_keys`, which has not been done and should be a deliberate, approved step (it creates a new Pi→Hetzner access path), not something to set up silently.

**Takeaway:** If a connector timeout traces back to a firewalled port rather than DNS/TLS/auth failure, check whether that port was intentionally excluded from the `ufw` allowlist before assuming it needs re-exposing — some restrictions (like this one) are deliberate security decisions, not gaps.
