# Skill: Refactor

A refactor changes structure, not behavior. If behavior changes, it's not a
refactor — it's a refactor _and_ a change, and they should be separate.

## Before starting

1. **Confirm the goal.** Refactors without a stated goal ("make it cleaner")
   tend to sprawl. Pin down what specifically should be easier _after_ this:
   "extracting X so we can mock it in tests," "removing duplication between
   A and B," etc.
2. **Check coverage.** Refactors are safe in proportion to test coverage of
   the code being touched. If coverage is thin, _add tests first_ — a
   characterization test that locks in current behavior, then refactor under
   it.
3. **Estimate the blast radius.** If the change touches more than ~10 files
   or any public API, surface that to the user before starting. They may
   want it split.

## Doing the refactor

- **One transformation per step.** Rename, then extract, then move — not all
  at once. Each step compiles and passes tests.
- **Mechanical changes first.** Renames and moves are low-risk; do them
  before the harder semantic changes.
- **Don't change behavior under the guise of refactoring.** No "while I'm
  here" bug fixes, no opportunistic API changes. Note them; address them
  separately.

## When you're done

- [ ] Test suite passes — the same tests that passed before.
- [ ] No new tests required (if you added new tests, behavior changed).
- [ ] The diff is reviewable file-by-file. If a reviewer would need to load
      it into their head all at once to understand it, split it.

## Report back

- One sentence on what's now easier.
- The list of follow-ups you intentionally _did not_ do in this refactor.
