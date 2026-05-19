# Thomas Schenkelberg - Claude Code marketplace

This repo is the **plugin marketplace** for Claude Code plugins built by Thomas Schenkelberg. Adding it once gives you access to every plugin listed below, plus anything added later.

## Install (two lines, once)

Open Claude Code and paste:

```
/plugin marketplace add thomas-schenkelberg/marketplace
/plugin install wrap-up@thomas-schenkelberg
```

From now on, the plugin's commands work in every project.

## What's in here

| Plugin | License | What it does |
|---|---|---|
| [`wrap-up`](https://github.com/thomas-schenkelberg/claude-code-wrap-up-plugin) | MIT | End-of-session housekeeping. `/wrap-up` commits touched repos and keeps each project's tracker / PRD / agent-instructions current. `/init-project` seeds those four files at project start. |

More plugins land here over time - once you've added the marketplace, new plugins show up in `/plugins` automatically (run `/plugin marketplace update thomas-schenkelberg` to refresh the catalogue).

## Updating

```
/plugin marketplace update thomas-schenkelberg
/plugin update wrap-up@thomas-schenkelberg
```

## Removing

```
/plugin uninstall wrap-up@thomas-schenkelberg
/plugin marketplace remove thomas-schenkelberg
```

## Migrating from the old install path

If you previously installed via `thomas-schenkelberg/claude-code-wrap-up-plugin` directly, switch to this marketplace once:

```
/plugin marketplace remove thomas-schenkelberg
/plugin marketplace add thomas-schenkelberg/marketplace
/plugin install wrap-up@thomas-schenkelberg
```

After that, updates work as usual.

## Author

Maintained by **tschenkster - Thomas Schenkelberg** ([LinkedIn](https://www.linkedin.com/in/thomas-schenkelberg/)), a fractional CFO who helps tech companies put AI to work in finance and operations.

## License

The marketplace manifest itself is MIT (see [LICENSE](./LICENSE)). Each plugin carries its own license - check the plugin's repo.
