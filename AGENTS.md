# Agent Instructions

> This file is the universal entry-point for AI coding agents working in this
> repo. It is intentionally short — heavy content lives in `.ai/` and is loaded
> on demand.

## Project

See [`.ai/project.md`](.ai/project.md) for: what this project is, the stack,
the entry points, how to run/test/build.

## Rules (must follow)

See [`.ai/rules.md`](.ai/rules.md) for the full do/don't list. The non-negotiables:

<!-- FILL: replace these with your project's hard rules. Keep this list short
     (5–10 items). Detailed rules go in .ai/rules.md. -->

1. Never commit secrets, credentials, or `.env` files.
2. Don't add dependencies without checking they're already covered by what's installed.
3. Match existing code style — don't reformat unrelated code.
4. Write the minimum code to satisfy the task. No speculative features.
5. Ask before making structural changes (renames, moves, deletions, schema changes).

## How to work in this repo

1. **Read first.** Before editing, read the file you're changing _and_ its
   nearest siblings. Patterns in this repo are local; don't apply generic
   defaults if a local convention exists.
2. **Match the patterns.** New code should look like the code next to it.
3. **Run the checks.** See `.ai/project.md` for the test/lint/typecheck
   commands. Run them before declaring work done.
4. **Small, reviewable changes.** One concern per change. Don't bundle drive-by
   refactors with feature work.

## When to load more context

| If you're about to…              | Read first                                        |
| -------------------------------- | ------------------------------------------------- |
| Touch architecture / data flow   | [`.ai/architecture.md`](.ai/architecture.md)      |
| Format code / pick names         | [`.ai/style.md`](.ai/style.md)                    |
| See an unfamiliar domain term    | [`.ai/glossary.md`](.ai/glossary.md)              |
| Add a new feature                | [`.ai/skills/add-feature.md`](.ai/skills/add-feature.md) |
| Fix a bug                        | [`.ai/skills/fix-bug.md`](.ai/skills/fix-bug.md)  |
| Refactor                         | [`.ai/skills/refactor.md`](.ai/skills/refactor.md) |
| Write tests                      | [`.ai/skills/write-tests.md`](.ai/skills/write-tests.md) |
| Question a past architectural choice | [`.ai/decisions/`](.ai/decisions/)            |

## Token discipline

This file plus the project + rules files are likely in your context on every
turn. Don't pull on-demand files unless you actually need them. Don't quote
large blocks of those files back to the user — link to them by path.
