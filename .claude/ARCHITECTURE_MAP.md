# Architecture Map

| Path | Contents |
|------|----------|
| `agents/` | Subagents (Markdown + YAML frontmatter: name, description, tools, model) |
| `skills/` | Curated skills (When to Use, How It Works, Examples) |
| `commands/` | Slash commands (`description:` frontmatter) |
| `hooks/` | Hook definitions (JSON: matcher + hooks array) |
| `rules/` | Always-follow guidelines |
| `mcp-configs/` | MCP server configurations |
| `scripts/` | CommonJS Node utilities; hooks in `scripts/hooks/`, helpers in `scripts/lib/` |
| `tests/` | Mirrors `scripts/`; `*.test.js`, runner `tests/run-all.js` |
| `docs/` | Guides and translations (on demand, see `docs/INDEX.md`) |
