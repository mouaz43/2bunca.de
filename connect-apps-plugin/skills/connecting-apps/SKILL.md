---
name: connecting-apps
description: "Use this skill when the user wants to connect, link, or integrate an external app or service with Claude (e.g. 'connect my Gmail', 'link Google Drive', 'add the GitHub integration', 'hook up Slack'), asks which apps are connected, or reports that a connected app is not working. Covers MCP servers and claude.ai connectors: discovering what is available, connecting new apps, and troubleshooting broken connections. Do NOT use for writing application code that calls third-party APIs directly."
---

# Connecting apps to Claude

## What "connected apps" means

Apps reach Claude through MCP (Model Context Protocol) servers. Their tools
show up in the session with names like `mcp__Gmail__search_threads` or
`mcp__github__create_pull_request`. On claude.ai and the desktop app these are
called "connectors"; in the CLI they are configured MCP servers.

## Checking what is connected

- Look at the tools available in the current session: every `mcp__<server>__*`
  prefix is one connected app.
- If a server is listed as "still connecting", wait or use ToolSearch with a
  relevant keyword rather than declaring it unavailable.
- Report only what you can actually see. Never guess connection status.

## Connecting a new app

Pick the instructions that match the user's surface:

- **claude.ai / desktop app**: Settings → Connectors → browse or add the app,
  then authorize it. If a connector-suggestion tool is available in the
  session, use it to surface an install card directly.
- **Claude Code CLI**: `claude mcp add <name> -- <command>` for a local stdio
  server, or `claude mcp add --transport http <name> <url>` for a remote one.
  Project-scoped servers go in `.mcp.json` at the repo root so teammates get
  them too.

## Troubleshooting

- Tools missing mid-session usually means the MCP server disconnected; it often
  reconnects on its own. Re-check before telling the user it is gone.
- Auth errors from connector tools mean the user needs to re-authorize the app
  in Settings → Connectors (or re-run the server's auth flow in the CLI).
- If a specific tool schema is not loaded, load it first (ToolSearch in
  sessions that use deferred tools) instead of calling it blind.
