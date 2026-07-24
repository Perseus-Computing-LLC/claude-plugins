# Perseus Computing — Claude Code Plugins

A [Claude Code](https://code.claude.com) plugin marketplace for **local-first context and memory** MCP servers:

| Plugin | What it does |
|--------|--------------|
| **perseus** | Live context engine — pre-resolves git, services, tests, and memory into a ready context briefing at session start (compile-before-context, not runtime tool calls). |
| **mimir** | Perseus Vault — local-first, encrypted (AES-256-GCM) persistent memory — 46 MCP tools over SQLite + FTS5 hybrid search, single Rust binary, fully offline. |

Both are MIT-licensed and run entirely on your machine.

## Install

Add the marketplace, then install either plugin:

```
/plugin marketplace add Perseus-Computing-LLC/claude-plugins
/plugin install perseus@perseus-computing
/plugin install mimir@perseus-computing
```

## Prerequisites

The plugins wire up the MCP servers but expect the underlying binaries on your `PATH`:

- **Perseus** — `pip install perseus-ctx` ([PyPI](https://pypi.org/project/perseus-ctx/))
- **Perseus Vault** — `curl -sSf https://raw.githubusercontent.com/Perseus-Computing-LLC/perseus-vault/main/scripts/install.sh | sh` (installs to `~/.local/bin/perseus-vault`, symlinked as `mimir`/`mneme` too)

## How it works

- **perseus** launches `perseus mcp serve --workspace ${CLAUDE_PROJECT_DIR}`, scoping context to your current project.
- **mimir** launches `mimir serve --db ${CLAUDE_PLUGIN_DATA}/mimir.db`, keeping the memory database in Claude Code's persistent plugin-data directory so it survives plugin updates.

After installing, confirm the servers are connected with `/mcp`.

## Links

- Perseus — https://github.com/Perseus-Computing-LLC/perseus
- Perseus Vault — https://github.com/Perseus-Computing-LLC/perseus-vault

---

© Perseus Computing LLC — MIT License
