# AI Coding Boilerplate

A drop-in project skeleton that makes any AI coding agent (Claude Code, Cursor,
GitHub Copilot, Windsurf, Cline, Aider, Codex, etc.) productive on your repo
with **one set of templates** instead of one config per tool.

## The idea

Most teams end up maintaining a `CLAUDE.md`, a `.cursorrules`, a
`copilot-instructions.md`, a `.windsurfrules`, and so on — each saying roughly
the same thing, each drifting out of sync.

This boilerplate flips that around:

```
.ai/              ← you edit this (source of truth)
AGENTS.md         ← short universal entry-point (auto-loaded by many agents)
CLAUDE.md         ← thin shim → points at AGENTS.md + .ai/
.cursorrules      ← thin shim → points at AGENTS.md + .ai/
.cursor/rules/    ← thin shim → points at AGENTS.md + .ai/
.github/copilot-instructions.md  ← thin shim
.windsurfrules    ← thin shim
.clinerules       ← thin shim
```

You only edit files in `.ai/` (and `AGENTS.md`). The agent-specific files are
already wired up and rarely need changes.

## Quick start

1. Open `.ai/project.md` and fill in the placeholders (`<!-- FILL: ... -->`).
2. Open `.ai/rules.md` and tune the rules for your stack.
3. Skim `.ai/style.md`, `.ai/architecture.md`, `.ai/glossary.md` — fill what's
   relevant, delete what isn't.
4. (Optional) Add project-specific workflows under `.ai/skills/`.
5. Commit. Every supported agent now reads the same instructions.

## Why this layout is token-efficient

Most agents inject their "rules" file into **every** turn. Putting 2,000 lines
of architecture docs there burns tokens on every message.

This boilerplate splits content by load frequency:

| File                    | Loaded            | Keep it…                              |
| ----------------------- | ----------------- | ------------------------------------- |
| `AGENTS.md`             | Every turn        | Tight: stack, hard rules, where-to-look |
| `.ai/project.md`        | Every turn        | Tight: what the project is             |
| `.ai/rules.md`          | Every turn        | Tight: do/don't list                   |
| `.ai/architecture.md`   | On demand         | As long as you need                    |
| `.ai/style.md`          | On demand         | As long as you need                    |
| `.ai/glossary.md`       | On demand         | As long as you need                    |
| `.ai/skills/*.md`       | On demand         | One per workflow                       |
| `.ai/decisions/*.md`    | On demand         | One per decision                       |

Always-loaded files are kept **short** — they tell the agent _what exists_ and
_where to look_. Heavy content lives in on-demand files the agent reads only
when relevant.

## Supported agents

| Agent              | Config file                              | Status |
| ------------------ | ---------------------------------------- | ------ |
| Claude Code        | `CLAUDE.md`                              | ✓ wired |
| Cursor             | `.cursorrules`, `.cursor/rules/*.mdc`    | ✓ wired |
| GitHub Copilot     | `.github/copilot-instructions.md`        | ✓ wired |
| Windsurf           | `.windsurfrules`                         | ✓ wired |
| Cline              | `.clinerules`                            | ✓ wired |
| Codex / Jules / OpenAI Agents | `AGENTS.md`                   | ✓ wired (native) |
| Aider              | `.aider.conf.yml` + `CONVENTIONS.md`     | ✓ wired |

Adding a new agent? Just create its config file and point it at `AGENTS.md` and
the relevant `.ai/*.md` files — see `.ai/README.md` for the recipe.

## What this boilerplate is **not**

- Not a code framework. It contains no application code, no `package.json`, no
  `requirements.txt`. Drop it into any repo regardless of language.
- Not a prompt collection. It's a place for _your_ rules, not generic prompts.
- Not opinionated about your stack. Templates are language-agnostic.

## Layout

```
.
├── README.md                          ← you are here
├── AGENTS.md                          ← universal agent entry-point
├── .ai/                               ← SOURCE OF TRUTH (edit these)
│   ├── README.md                      ← how the .ai/ folder works
│   ├── project.md                     ← what the project is
│   ├── rules.md                       ← coding rules (do / don't)
│   ├── architecture.md                ← system architecture
│   ├── style.md                       ← code style guide
│   ├── glossary.md                    ← domain terms
│   ├── skills/                        ← reusable workflows
│   │   ├── README.md
│   │   ├── add-feature.md
│   │   ├── fix-bug.md
│   │   ├── refactor.md
│   │   └── write-tests.md
│   └── decisions/                     ← architecture decision records
│       ├── README.md
│       └── TEMPLATE.md
│
├── CLAUDE.md                          ← Claude Code shim
├── CONVENTIONS.md                     ← Aider shim
├── .aider.conf.yml                    ← Aider config
├── .cursorrules                       ← Cursor (legacy) shim
├── .cursor/rules/project.mdc          ← Cursor (modern) shim
├── .github/copilot-instructions.md    ← GitHub Copilot shim
├── .windsurfrules                     ← Windsurf shim
└── .clinerules                        ← Cline shim
```
