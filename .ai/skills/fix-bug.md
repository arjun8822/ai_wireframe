# Skill: Fix a bug

## Before changing code

1. **Reproduce it first.** Don't trust the report verbatim — run the failing
   scenario yourself (or write a failing test). If you can't reproduce, say
   so and ask for more info before changing code.
2. **Find the root cause, not the symptom.** A bug that "looks fixed" because
   you added a null check often just moves the problem one layer up. Trace
   it back to where the bad state was introduced.
3. **Resist the urge to refactor.** A bug fix changes the smallest amount of
   code that makes the test pass. Cleanup goes in a separate change.

## Implementation

1. **Write a failing test that captures the bug.** This is the regression
   test. It should fail without your fix and pass with it.
2. **Make the smallest change that turns the test green.**
3. **Don't change the test once it's passing.** If you find yourself
   tweaking the test, you're testing the implementation, not the behavior.

## Special cases

- **The bug is in third-party code.** Look for an open issue/changelog; if a
  newer version fixes it, prefer upgrading over patching. If you must patch,
  isolate the workaround and link the upstream issue in a comment.
- **The bug is in a test, not the code.** Confirm before "fixing" it — a
  failing test might be telling the truth.
- **You can't find the root cause.** Say so. A speculative fix is worse than
  a documented unknown.

## Report back

- The root cause in one sentence.
- The test you added.
- Anything related you noticed but did _not_ fix (so it doesn't get lost).
