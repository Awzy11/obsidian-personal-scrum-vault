# Claude Code Setup

This guide covers how to connect Claude Code to your Obsidian vault via the Obsidian MCP server, enabling AI-assisted sprint planning, daily standups, and knowledge management directly from your terminal.

This is **entirely optional.** The vault works without any of this. Come back here when you want to level up.

---

## What This Unlocks

Once set up, you can ask Claude Code things like:
- "Run my beginning-of-week sprint planning" — pulls backlog, opens weekly note, helps you prioritize
- "Do my end-of-day closeout" — reviews today's note, moves captures to inbox, updates backlog
- "Add this to my inbox" — creates a tagged inbox note without opening Obsidian
- "What's in my backlog this week?" — reads and summarizes your sprint state
- "Create a note about [idea]" — captures a permanent note directly into `50 - Notes/`

---

## Prerequisites

1. **Obsidian** installed and this vault open
2. **Obsidian Local REST API** plugin installed and enabled
3. **Claude Code** installed (`npm install -g @anthropic-ai/claude-code`)
4. **Docker** installed (for running the MCP server container)
5. **mcp-proxy** installed (`pipx install mcp-proxy`)

---

## Step 1 — Install the Obsidian REST API Plugin

1. In Obsidian: Settings → Community Plugins → Browse
2. Search for **"Local REST API"** (by Adam Coddington)
3. Install and enable it
4. Go to Settings → Local REST API
5. Copy your **API key** — you'll need it in Step 3
6. Note the **port** (default: `27123`)
7. Make sure **"Enable Non-Encrypted (HTTP) Server"** is on for local use

---

## Step 2 — Run the MCP Server

The Obsidian MCP server runs as a Docker container that bridges Claude Code to the Obsidian REST API.

```bash
docker run -i --rm \
  -e OBSIDIAN_API_KEY="YOUR_API_KEY_HERE" \
  -e OBSIDIAN_HOST="localhost" \
  -e OBSIDIAN_PORT="27123" \
  mcp/obsidian
```

To run it persistently (recommended), set it up as a background service. On Linux with systemd:

```ini
# ~/.config/systemd/user/mcp-obsidian.service
[Unit]
Description=Obsidian MCP Server
After=network.target

[Service]
ExecStart=/home/YOUR_USERNAME/.local/bin/mcp-proxy --port 8091 -- \
  docker run -i --rm \
  -e OBSIDIAN_API_KEY="YOUR_API_KEY_HERE" \
  -e OBSIDIAN_HOST="localhost" \
  -e OBSIDIAN_PORT="27123" \
  mcp/obsidian
Restart=on-failure
RestartSec=5

[Install]
WantedBy=default.target
```

Enable and start:
```bash
systemctl --user enable mcp-obsidian
systemctl --user start mcp-obsidian
```

---

## Step 3 — Configure Claude Code

Add the MCP server to your Claude Code config at `~/.claude.json`:

```json
{
  "mcpServers": {
    "obsidian": {
      "type": "sse",
      "url": "http://localhost:8091/sse"
    }
  }
}
```

Restart Claude Code. You should see the Obsidian MCP tools available in your session.

---

## Step 4 — Customize CLAUDE.md

Open `CLAUDE.md` in the vault root and fill in every `YOUR_*` placeholder with your actual context:

- Your role and work priorities
- Your active projects
- Your personal goals
- Your preferred tools

The more accurately CLAUDE.md reflects your real situation, the more useful Claude's assistance will be. This file is read at the start of every Claude Code session.

---

## Vault on a Remote Machine

If your Obsidian vault runs on a separate machine (e.g., a home server or Raspberry Pi):

1. Change `OBSIDIAN_HOST` in the Docker command to the server's local IP (e.g., `192.168.1.100`)
2. Make sure port `27123` is reachable from the machine running Claude Code
3. For remote access outside your LAN, use Tailscale and set `OBSIDIAN_HOST` to the Tailscale IP

---

## Verifying the Connection

In a Claude Code session, ask:

> "List the files in my Obsidian vault root"

If the MCP tools are connected, Claude will call `obsidian_list_files_in_vault` and return your vault structure. If it errors, check:

1. Is the REST API plugin enabled in Obsidian?
2. Is the MCP server container running? (`docker ps`)
3. Is the port in `~/.claude.json` matching the port `mcp-proxy` is listening on?
4. Is the API key correct?

---

## Building Workflow Automations

Once connected, you can create custom slash commands (Claude Code skills) for repeatable workflows. Examples from the vault author's setup:

- `/bow` — Beginning of week: opens backlog, creates weekly note, runs sprint planning
- `/bod` — Beginning of day: opens current sprint, creates daily note, sets Today's 3
- `/eod` — End of day: reviews captures, processes inbox, updates backlog
- `/eow` — End of week: sprint review, retrospective, archives completed items

To create your own, see the [Claude Code documentation](https://docs.anthropic.com/claude-code) on custom slash commands and skills.

---

## Related

- [[CLAUDE.md]] — vault context file for Claude Code
- [[Daily Note Workflow]] — the workflow these automations support
- [[Personal Scrum]] — sprint methodology reference
