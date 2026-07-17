---
description: List connected apps (MCP servers/connectors) and help connect a new one
argument-hint: "[app name, e.g. gmail, google drive, slack]"
---

Help the user connect apps to Claude Code.

1. First, take stock of what is already connected: check which MCP servers and
   connector tools are currently available in this session (tools prefixed with
   `mcp__`). Summarize them by app in a short list.
2. If the user named an app in "$ARGUMENTS", focus on that app:
   - If it is already connected, say so and show 2-3 example things they can ask
     for with it.
   - If it is not connected, explain the best way to connect it on their
     surface: on claude.ai / desktop via Settings → Connectors; in the CLI via
     `claude mcp add` or a `.mcp.json` entry in the project. If a connector
     suggestion tool (e.g. SuggestConnectors) is available, use it.
3. If no app was named, list what is connected, mention 2-3 popular apps they
   could connect (Gmail, Google Drive, GitHub, Slack), and ask which one they
   want.
4. Never invent connection status — only report servers/tools you can actually
   see in the session.
