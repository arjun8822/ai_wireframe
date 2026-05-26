# GitHub Copilot Instructions

GitHub Copilot reads this file as repository-wide custom instructions. The
real source of truth for this project's AI guidance lives in `AGENTS.md` and
the `.ai/` folder — Copilot doesn't auto-import them, so the most important
points are summarized below. **Edit `.ai/`, not this file.** Then re-summarize
here only if the top rules change.

## Project

See [`/AGENTS.md`](../AGENTS.md) and [`/.ai/project.md`](../.ai/project.md)
for project description, stack, and run/test commands. Read those before
suggesting code that depends on stack-specific details (framework version,
package manager, lint config).

## Hard rules (from `.ai/rules.md`)

- Never commit secrets, `.env` files, API keys, tokens, or credentials.
- Don't add dependencies casually — check that the project doesn't already
  cover the need.
- Match existing code style. Don't reformat unrelated code. Don't reorder
  imports outside the file you're editing.
- Write the minimum code that satisfies the task. No speculative
  abstractions, no "we might need this later" helpers.
- Don't bypass safety checks (`--no-verify`, disabling types) to push work
  through. Fix the underlying issue.

## When suggesting code

- Read the file you're editing and its sibling files first. Patterns are
  local; the rest of the codebase is the authoritative style guide.
- Comments explain **why**, not **what**. Default to no comment.
- For tests, see [`/.ai/skills/write-tests.md`](../.ai/skills/write-tests.md).
- For architecture-shaped changes, consult
  [`/.ai/architecture.md`](../.ai/architecture.md).
