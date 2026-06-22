# AGENTS.md: thomas-schenkelberg/marketplace

> Project instructions for any coding agent working on this repo.

**Maintainer:** thomasschenkelberg (Thomas Schenkelberg | https://www.linkedin.com/in/thomas-schenkelberg/). MIT licensed.

## What this project is

The **Claude Code plugin marketplace** for everything Thomas publishes. Installing this marketplace once gives a user access to every plugin in the catalog (currently just `wrap-up`; more land here over time). The marketplace `name` field is `thomas-schenkelberg`, so the install command reads `/plugin install <plugin>@thomas-schenkelberg`.

This repo is a manifest, not code. There is no runtime, no build step, no tests beyond a `jq` parse of the JSON.

## Repository layout

```
.claude-plugin/marketplace.json   the manifest — name, description, owner, plugins[]
README.md                          the public-facing install + catalog page
LICENSE                            MIT, attribution: thomasschenkelberg (Thomas Schenkelberg | …)
AGENTS.md  CLAUDE.md  _tracker.md  this file + companions (project-setup rule Tier 0)
.gitignore
```

The plugins themselves live in separate GitHub repos (e.g. `thomas-schenkelberg/claude-code-wrap-up-plugin`). Each plugin entry in `marketplace.json` references its repo via a `url`-typed source with `ref: "main"` (no SHA pin, so users get the latest commit automatically).

## How to add a new plugin

1. Confirm the plugin repo is public (or, for paid `cfo-toolkit-*` plugins, follow the per-client outside-collaborator model — those do NOT belong in this public marketplace).
2. Edit `.claude-plugin/marketplace.json` — append a new object to `plugins[]` with: `name`, `description`, `source` (`{ source: "url", url, ref: "main" }`), `category`, `homepage`, `license`, `keywords`.
3. Validate locally: `jq . .claude-plugin/marketplace.json`.
4. Commit with the standard co-author trailer and push to `main`.
5. Installed users see the new plugin after `/plugin marketplace update thomas-schenkelberg`.
6. Update the README's "What's in here" table.

## How to test locally (when the marketplace itself changes)

1. In a scratch project: `/plugin marketplace remove thomas-schenkelberg` (if already added), then `/plugin marketplace add /absolute/path/to/marketplace` — pointing at this local clone, not the GitHub URL.
2. `/plugin install <plugin>@thomas-schenkelberg` for each plugin you want to verify.
3. Exercise the plugins in a throwaway folder.
4. When done: `/plugin marketplace remove thomas-schenkelberg`, then re-add the GitHub version.

## Conventions

- **Manifest only.** No code, no scripts, no CI. If logic is needed, it belongs in a plugin repo, not here.
- **`ref: "main"` not SHA-pinned** for every plugin source — solo-dev marketplace, latest is fine. Pin to a SHA only if a specific plugin needs reproducibility.
- **Public funnel pieces only.** Paid `cfo-toolkit-*` plugins live in their own private repos with per-client outside-collaborator grants. Listing them here would leak the catalog.
- **Brand standard.** Public-facing prose (README, descriptions in `marketplace.json`) uses space-hyphen-space, not em-dashes (`feedback_em_dash_lint_before_send`).
- **Attribution signature** in LICENSE / `marketplace.json` owner / README: `thomasschenkelberg (Thomas Schenkelberg | https://www.linkedin.com/in/thomas-schenkelberg/)` (`feedback_repo_license_attribution`).
