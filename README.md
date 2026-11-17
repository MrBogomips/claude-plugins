# mrbogomips — Claude Code plugin marketplace

One marketplace for the Claude Code plugins by MrBogomips. Each plugin lives in its own
repository; this repository only lists them.

## Install

```
/plugin marketplace add MrBogomips/claude-plugins
/plugin install <plugin>@mrbogomips
```

From a terminal:

```bash
claude plugin marketplace add MrBogomips/claude-plugins
claude plugin install <plugin>@mrbogomips
```

## Plugins

| Plugin | Repository | What it does |
|--------|------------|--------------|
| `skills` | [MrBogomips/skills](https://github.com/MrBogomips/skills) | General-purpose agent skills: handoff, done, pause, tldr, the AGENTS.md family, Gemini web research, image generation. Invoked as `/skills:<name>`. |
| `eng-artifacts` | [MrBogomips/eng-artifacts](https://github.com/MrBogomips/eng-artifacts) | Optimized production of software engineering artifacts (entity relationship diagrams first) as self-contained HTML pages with one visual language, light/dark and replaceable themes. Invoked as `/eng-artifacts:<name>`, or picked up from a plain request. |

Claude Code installs a plugin as a whole: `skills@mrbogomips` brings every skill in the set. To
install a single skill, in Claude Code or in another agent, use the
[skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add MrBogomips/skills --skill <name>
```

## Updating

The marketplace does not pin plugin versions: each plugin's version comes from the
`plugin.json` in its own repository. Refresh with:

```
/plugin marketplace update mrbogomips
```

## License

[MIT](LICENSE)
