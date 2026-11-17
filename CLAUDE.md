# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## What this repository is

The `mrbogomips` Claude Code marketplace. It contains no plugin code: the only functional file
is `.claude-plugin/marketplace.json`, which lists plugins hosted in their own repositories.
`README.md` is the user-facing install guide and must list the same plugins as the manifest.

Users install with `/plugin marketplace add MrBogomips/claude-plugins` and
`/plugin install <plugin>@mrbogomips`.

## Commands

```bash
# Validate the manifest (must pass before every commit)
claude plugin validate . --strict

# Install test in an isolated config that leaves the real ~/.claude untouched
export CLAUDE_CONFIG_DIR=$(mktemp -d)
claude plugin marketplace add "$PWD"          # local working copy; or MrBogomips/claude-plugins after push
claude plugin install <plugin>@mrbogomips
claude plugin list                            # expect <plugin>@mrbogomips with the version from its plugin.json
rm -rf "$CLAUDE_CONFIG_DIR"
```

## Rules for plugin entries

- **No `version` in an entry.** The version is read from the `plugin.json` in the plugin's own
  repository, so releasing a plugin never requires a change here.
- **Sources:** `{"source": "github", "repo": "MrBogomips/<repo>"}` for a plugin at a repo root;
  `git-subdir` with `url` and `path` for a plugin in a subfolder (e.g. the plugins of
  `MrBogomips/claude-code`). Use `ref`/`sha` only for a temporary test against an unmerged
  branch, and remove it before committing.
- **Only installable, public repos.** A GitHub source works only if the repo, as committed,
  holds everything the plugin needs at runtime, and only for users with git access to it.
- Plugin names must not start with `claude-`, `anthropic-`, `anthropics-`, `cc-plugin-`.
- Reference: https://code.claude.com/docs/en/plugins/marketplace-reference.md

## Duplicate marketplaces

Several MrBogomips repos still publish their own marketplace (`eng-artifacts`, `mrbogomips-tools`
in `claude-code`). When one of their plugins is added
here, a user who has both marketplaces sees it twice: propose removing the per-repo marketplace,
through a PR in that repo. `MrBogomips/skills` and `MrBogomips/harness-maker` (formerly `agentic-harness`, whose
`mrbogomips-harness` marketplace was removed in 0.12.0) have no marketplace of their own.

Installations cannot be moved between marketplaces (`renames` works only within one
marketplace): users must uninstall from the old marketplace and reinstall from `mrbogomips`.

Not listed yet, and why:
- `askboard`: its `dist/` is gitignored, so a GitHub source would install without the built
  server.
- `aios`: private repo. `everything-claude-code`: a fork, never listed.

## Conventions

- Conventional commits (`feat:`, `fix:`, `docs:`, `chore:` …).
- Base branch: `main`.
