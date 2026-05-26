# `.ai/` — Source of Truth for AI Agents

Everything in this folder is the single source of truth that every AI coding
agent (Claude Code, Cursor, Copilot, Windsurf, Cline, Aider, …) reads from.

You edit files here. The agent-specific config files at the repo root
(`CLAUDE.md`, `.cursorrules`, etc.) are thin shims that point _into_ this
folder — they generally don't need touching.

## File map

| File                  | Purpose                                       | Loaded?              |
| --------------------- | --------------------------------------------- | -------------------- |
| `project.md`          | What the project is, stack, how to run/test   | **Always** (small)   |
| `rules.md`            | Coding rules (do / don't list)                | **Always** (small)   |
| `architecture.md`     | System architecture, data flow, key modules   | On demand            |
| `style.md`            | Code style, naming, formatting                | On demand            |
| `glossary.md`         | Domain-specific terms                         | On demand            |
| `skills/`             | Step-by-step workflows for common tasks       | On demand (per task) |
| `decisions/`          | ADRs — why we made each architectural choice  | On demand            |

## Conventions for editing these files

- **Placeholders** look like `<!-- FILL: short description -->`. Replace them
  with project specifics, then delete the comment.
- **Keep always-loaded files short.** `project.md` and `rules.md` are in the
  agent's context on every turn. Long always-loaded docs = wasted tokens on
  every message and worse model focus.
- **Push detail to on-demand files.** When `rules.md` says "follow our test
  conventions," link to a detailed section in `style.md` or a skill in
  `skills/`. The agent loads the deeper file only when relevant.
- **Use links, not duplication.** Cross-reference with relative paths so the
  agent can navigate, and so updates only happen in one place.
- **Date your decisions.** Files under `decisions/` should include the date.
  Treat them as immutable once accepted — write a new ADR to supersede an old
  one.

## Adding a new agent

If you want to support an agent not already wired up:

1. Find that agent's expected config file (e.g. `.newagent/config.md`).
2. Create it with the same shim pattern as `CLAUDE.md` — a few sentences
   delegating to `AGENTS.md` and the relevant `.ai/` files.
3. Add it to the table in the root `README.md`.

Most agents now auto-load `AGENTS.md` as a fallback, so often no shim is
needed at all.

## Adding a new skill

Skills are short, scenario-specific playbooks. To add one:

1. Copy an existing file in `skills/` as a template.
2. Title it after the task (e.g. `add-migration.md`, `update-api-client.md`).
3. List it in `skills/README.md` and link it from `AGENTS.md`'s "When to load
   more context" table if it's frequently needed.

Keep each skill self-contained: a reader pulling _only_ that skill should have
enough context to do the task.
