# Claude Code Instructions

This file is auto-loaded by Claude Code on every turn. It is intentionally
short — the source of truth lives in `AGENTS.md` and the `.ai/` folder.

## Read first

- @AGENTS.md — the universal agent entry-point (project summary, top rules,
  pointers to deeper docs)
- @.ai/project.md — what this project is, stack, run/test commands
- @.ai/rules.md — hard do/don't rules

## Load on demand

Pull these in only when relevant to the current task:

- @.ai/architecture.md — when touching structure or data flow
- @.ai/style.md — when picking names, writing comments, formatting
- @.ai/glossary.md — when you see an unfamiliar domain term
- @.ai/skills/ — task-specific playbooks (add-feature, fix-bug, refactor,
  write-tests)
- @.ai/decisions/ — context on why past architectural calls were made

## Claude-specific notes

- The `@path` syntax above is a Claude Code import — these files are pulled
  into context automatically.
- For deep work, prefer launching subagents with the `Explore` or
  `general-purpose` types so research stays out of the main context.
- TaskCreate is the right tool for multi-step work in this repo.
