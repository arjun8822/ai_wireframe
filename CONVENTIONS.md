# Conventions (for Aider)

Aider auto-loads this file when configured (see `.aider.conf.yml`). It is a
thin shim — the source of truth lives in `AGENTS.md` and the `.ai/` folder.

## Read first

- [`AGENTS.md`](AGENTS.md) — universal agent entry-point (project summary,
  top rules, pointers to deeper docs)
- [`.ai/project.md`](.ai/project.md) — project description, stack,
  run/test/build commands
- [`.ai/rules.md`](.ai/rules.md) — hard do/don't rules

## Read on demand

- [`.ai/architecture.md`](.ai/architecture.md) — structural changes
- [`.ai/style.md`](.ai/style.md) — naming / formatting / comments
- [`.ai/glossary.md`](.ai/glossary.md) — domain terms
- [`.ai/skills/`](.ai/skills/) — task-specific playbooks
- [`.ai/decisions/`](.ai/decisions/) — past architectural choices

## Behavior

- The "Never" list in `.ai/rules.md` is non-negotiable.
- Match local patterns. Read neighbor files before editing.
- Smallest correct change. No speculative abstractions or scope creep.
- Run lint, typecheck, and tests (commands in `.ai/project.md`) before
  declaring work done.
