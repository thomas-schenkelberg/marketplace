# CLAUDE.md: thomas-schenkelberg/marketplace

@AGENTS.md

> Claude Code reads this file (not `AGENTS.md` directly). The `@AGENTS.md` line above imports it.

## Claude-specific notes

- **No code in this repo.** Don't add scripts, CI, or build steps. If you reach for one, the logic belongs in a plugin repo.
- **`marketplace.json` is the only file that matters.** Edits there must keep it valid JSON (`jq . .claude-plugin/marketplace.json` before commit).
- **Preferred model:** whatever the user is on; nothing in this repo needs a specific model.
