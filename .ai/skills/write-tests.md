# Skill: Write tests

## What to test

Test **behavior**, not implementation. A good test asks:

> "Given this input / state, does the system do the right thing for the user?"

Bad tests ask:

> "Does this function call that function with those arguments?"

The second kind breaks on every refactor without catching real bugs.

## Test pyramid (project guidance)

<!-- FILL: tune to your project. Defaults below are reasonable. -->

- **Unit** — Pure functions and small isolated modules. Fast, lots of them.
- **Integration** — Multiple modules together, real DB, real HTTP layer.
  Mock only external network calls. These catch the most real bugs.
- **End-to-end** — Browser/UI level. Few of these; reserve for critical
  paths only (sign-up, checkout, etc.). They're slow and flaky.

When in doubt, write the integration test. It's the highest signal-to-cost
ratio.

## Structure

- **Arrange → Act → Assert.** Blank lines between sections; no comments
  needed.
- **One behavior per test.** If you need "and" in the test name, split it.
- **Test names describe behavior in plain English**, not the method being
  called: `it("returns 401 when the token is expired")`, not
  `it("validateToken handles expiry")`.

## Things to avoid

- **Snapshot tests for things humans wouldn't read carefully.** A 200-line
  snapshot diff in a PR will be rubber-stamped. If you can't review the
  snapshot, the test isn't really running.
- **Mocking your own code.** If you're stubbing functions from this repo,
  you're testing the mock, not the code. Mock at the system boundary
  (network, filesystem, clock, randomness).
- **Tests that depend on each other or on ordering.** Each test sets up its
  own state.
- **Tests that depend on real time.** Inject the clock; freeze it in tests.
- **Asserting on log output**, unless logging is the feature.

## What "passing" means

A green test suite isn't proof the feature works. Before declaring done:

1. The new test fails when the change is reverted (the test actually
   exercises the code).
2. The feature has been manually exercised at least once (for UI changes).
3. Lint and typecheck also pass (see [`../project.md`](../project.md)).
