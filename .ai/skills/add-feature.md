# Skill: Add a feature

Use when adding any net-new user-visible behavior.

## Before writing code

1. **Confirm scope.** Restate to the user what you understand the feature to
   be in one paragraph. If anything is ambiguous, ask — don't guess.
2. **Find precedent.** Locate the most similar existing feature in the
   codebase. Read it end-to-end (UI → API → service → data layer → test).
   Your new feature should mirror its structure unless there's a reason not
   to.
3. **Identify the data shape.** What new fields/tables/types does this need?
   If a schema change is involved, surface that to the user before writing
   code — it usually wants its own PR.
4. **Plan in your head, not in a doc.** Don't create planning markdown files
   for the user to read. Just say what you'll do in a few sentences.

## Implementation order

Build outside-in, but ship inside-out. That is:

1. **Sketch the data layer first.** Types, schema, persistence.
2. **Then the service / domain logic.** Pure functions where possible.
3. **Then the API surface.** Route handlers, validation.
4. **Then the UI.** Components, forms, navigation.
5. **Tests alongside each layer**, not all at the end.

## Quality checklist (run before declaring done)

- [ ] All commands in [`../project.md`](../project.md) pass: lint, typecheck,
      tests.
- [ ] New behavior has at least one test that would fail without the change.
- [ ] No drive-by edits to unrelated files.
- [ ] No new top-level dependencies added without asking.
- [ ] No `console.log`, `print()`, or commented-out code left behind.
- [ ] Manually exercised the feature in the running app (for UI changes).

## What to report back

Keep it short:

- One sentence: what now works that didn't before.
- The list of files changed (the user has the diff — don't paste it).
- Anything notable: a deferred follow-up, an existing bug you spotted but
  didn't fix, an assumption you made.
