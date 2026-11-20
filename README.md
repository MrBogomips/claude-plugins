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
| `eng-skills` | [MrBogomips/eng-skills](https://github.com/MrBogomips/eng-skills) | Skills and agents for engineering work, technical writing first: doc comments, API references, OpenAPI descriptions, error messages, user manuals, release notes and implementation comments written for the audience each text reaches. Requirement and ticket IDs stay out of published text and traceability stays in implementation comments; it recognises when a UML, C4, ERD or BPMN diagram should go with the text. Ships a leak scanner and the `documentation-writer` and `documentation-reviewer` agents. Invoked as `/eng-skills:technical-writing`, or picked up from a plain request. |
| `harness-maker` | [MrBogomips/harness-maker](https://github.com/MrBogomips/harness-maker) | Stands up, assesses and maintains an agentic harness in an existing repo: project-specific agent teams, the skills they use and an orchestrator, with advisors for spec systems, issue trackers and visuals, and a machine check for the tools a harness needs. Invoked as `/harness-maker:<name>`. Formerly `agentic-harness@mrbogomips-harness`: uninstall that and install this. |
| `kaizen` | [MrBogomips/skills](https://github.com/MrBogomips/skills/tree/main/kaizen) (`kaizen/`) | Session retrospective: links the errors, reworks and ambiguities of a session to the skills, rules, CLAUDE.md, memory, hooks and settings behind them, and applies only reviewed fixes you authorize; a Stop hook offers it after a session with friction. Invoked as `/kaizen`. Formerly `kaizen@mrbogomips-tools`: uninstall that and install this. |
| `personal-voice` | [MrBogomips/skills](https://github.com/MrBogomips/skills/tree/main/personal-voice) (`personal-voice/`) | Writes documents, emails and messages in your tone and lexicon, learns from your revisions and own texts, and maintains the profile with per-item approval. Invoked as `/personal-voice:voice-write`, `voice-learn`, `voice-maintain` (renamed from `write`, `learn`, `maintain` in 1.0.0). Formerly `personal-voice@mrbogomips-tools`: uninstall that and install this. |
| `session-hub` | [MrBogomips/agent-orchestration](https://github.com/MrBogomips/agent-orchestration/tree/main/session-hub) (`session-hub/`) | From a master session in a hub of repositories, starts one child session per repository with a written scope (enforced by a fail-closed hook), a model and an effort level; children talk only to the master, which routes out-of-scope requests and keeps a record of them. Invoked as `/session-hub:spawn`, `dispatch`, `setup`. Replaces `spawn-session` from the `skills` plugin. |
| `model-router` | [MrBogomips/agent-orchestration](https://github.com/MrBogomips/agent-orchestration/tree/main/model-router) (`model-router/`) | Picks the model and effort for subagents, child sessions and workflows from one written grid, with task-class tags and per-project defaults. Invoked as `/model-router:choose-model`, `setup`. Measuring and adapting come in later releases. |
| `pm-artifacts` | [MrBogomips/pm-artifacts](https://github.com/MrBogomips/pm-artifacts) | Decision boards for project managers as self-contained HTML pages: an agile board with sprints and capacity, epics, roadmap, progress with release fit and people allocation, plus the findings to decide on. Editable and saved in place when published as an artifact. Invoked as `/pm-artifacts:agile-board`, or picked up from a plain request. |
| `skill-maker` | [MrBogomips/skills](https://github.com/MrBogomips/skills/tree/main/skill-maker) (`skill-maker/`) | Opinionated tools for producing quality skills and plugins, starting with short public READMEs that follow one fixed structure: inventories a plugin and its skills, checks and drafts each README against a fixed section contract, with an independent fact reviewer agent and a final validation script. Invoked as `/skill-maker:skill-readme`. |

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
