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
| `harness-maker` | [MrBogomips/harness-maker](https://github.com/MrBogomips/harness-maker) | Stands up, assesses and maintains an agentic harness in an existing repo: project-specific agent teams, the skills they use and an orchestrator, with advisors for spec systems, issue trackers and visuals, and a machine check for the tools a harness needs. Invoked as `/harness-maker:<name>`. Formerly `agentic-harness@mrbogomips-harness`: uninstall that and install this. |
| `kaizen` | [MrBogomips/skills](https://github.com/MrBogomips/skills/tree/main/kaizen) (`kaizen/`) | Session retrospective: links the errors, reworks and ambiguities of a session to the skills, rules, CLAUDE.md, memory, hooks and settings behind them, and applies only reviewed fixes you authorize; a Stop hook offers it after a session with friction. Invoked as `/kaizen`. Formerly `kaizen@mrbogomips-tools`: uninstall that and install this. |
| `personal-voice` | [MrBogomips/skills](https://github.com/MrBogomips/skills/tree/main/personal-voice) (`personal-voice/`) | Writes documents, emails and messages in your tone and lexicon, learns from your revisions and own texts, and maintains the profile with per-item approval. Invoked as `/personal-voice:voice-write`, `voice-learn`, `voice-maintain` (renamed from `write`, `learn`, `maintain` in 1.0.0). Formerly `personal-voice@mrbogomips-tools`: uninstall that and install this. |

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
