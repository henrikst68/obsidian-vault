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
