---
tags:
  - infrastructure
  - hetzner
  - mcp
  - obsidian
updated: '2026-05-30'
---
## Hetzner VPS Setup

**Server:** CAX11 (ARM64, Ampere Altra), Ubuntu 24.04 LTS
**Domain:** mcp.magleblik.dk
**Vault path:** /home/henrik/obsidian/personal
**GitHub repo:** github.com/henrikst68/obsidian-vault

## Stack

```
claude.ai → mcp.magleblik.dk → Caddy → supergateway (localhost:3100) → @bitbonsai/mcpvault → /home/henrik/obsidian/personal
```

## Systemd Service

File: `/etc/systemd/system/obsidian-mcp.service`

```ini
ExecStart=/usr/bin/npx supergateway --stdio "npx @bitbonsai/mcpvault /home/henrik/obsidian/personal" --port 3100 --cors --outputTransport streamableHttp
```

Commands:
```bash
systemctl daemon-reload
systemctl restart obsidian-mcp
systemctl status obsidian-mcp
```

## Caddy

Reverse proxies mcp.magleblik.dk → localhost:3100. Auto TLS via Let's Encrypt.

## Git Sync (Cron)

Pull (every 10 min): `*/10 * * * * cd /home/henrik/obsidian/personal && git pull --ff-only`
Push (every 5 min): `*/5 * * * * /home/henrik/obsidian/sync-push.sh >> /home/henrik/obsidian/sync-push.log 2>&1`

Push script: `/home/henrik/obsidian/sync-push.sh`

## Local PC Vault

Path: `C:\Users\micro\~\ObsidianVault`
Sync: `git pull` from GitHub

## MCP Access

Claude has vault-only MCP access (read/write notes, no shell).
To add shell access: install a shell MCP server on Hetzner and register it in claude.ai connectors.
