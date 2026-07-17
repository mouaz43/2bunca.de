# connect-apps-plugin

A small Claude Code plugin for discovering, connecting, and troubleshooting
app connections (MCP servers and claude.ai connectors).

## Usage

Load it for a session:

```bash
claude --plugin-dir ./connect-apps-plugin
```

Then:

- `/connect-apps` — list currently connected apps and get help connecting more
- `/connect-apps gmail` — check/connect a specific app

The bundled `connecting-apps` skill also triggers automatically when you ask
things like "connect my Gmail" or "why isn't Google Drive working?".

## What's inside

- **[connect-apps-plugin/connect-apps](https://github.com/mouaz43/2bunca.de/tree/main/connect-apps-plugin/commands/connect-apps.md)** - Slash command that lists connected apps and walks you through connecting new ones
- **[connect-apps-plugin/connecting-apps](https://github.com/mouaz43/2bunca.de/tree/main/connect-apps-plugin/skills/connecting-apps)** - Skill that handles connect/link/integrate requests and connection troubleshooting

## Related

- **[anthropics/skills](https://github.com/anthropics/skills)** - Official Anthropic skills collection (the `docx` skill in this repo was installed from it)
