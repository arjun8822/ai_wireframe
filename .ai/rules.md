# Rules

> Hard rules for working in this repo. Keep this list focused (aim for under
> ~50 lines of rules). Long explanations go in `style.md` or a skill — link to
> them instead.

## Always

<!-- FILL: things the agent should always do. Each rule = one line.
     Add a short "why" only when it isn't obvious. -->

- **Read before you write.** Open the target file _and_ its sibling files
  before editing. Match local patterns over generic best practices.
- **Match existing style.** Don't reformat unrelated code. Don't reorder
  imports unless the file is yours.
- **Run the checks.** Before declaring work done, run the lint + typecheck +
  tests listed in [`project.md`](project.md).
- **Use the package manager.** Add deps via the project's package manager
  (see `project.md`), not by hand-editing the lockfile.
- **Small commits, one concern each.** Don't bundle a refactor into a feature
  PR.

## Never

<!-- FILL: hard prohibitions. -->

- **Don't commit secrets.** No `.env`, no API keys, no tokens, no `.pem`,
  no service-account JSON. If a secret appears in a diff, stop.
- **Don't add dependencies casually.** Check whether existing libraries
  already cover the need before installing something new.
- **Don't introduce speculative abstractions.** No "we might need this later"
  helpers, base classes, or config options. Build for the current requirement.
- **Don't bypass safety checks** (`--no-verify`, disabling type checks,
  skipping tests) to push work through. Fix the underlying issue.
- **Don't delete or rename files without confirmation.** These are
  hard-to-reverse and frequently break things you can't see.
- **Don't write comments that restate the code.** Comments explain _why_,
  not _what_. See [`style.md`](style.md) for details.

## Ask before

<!-- FILL: things that need a human decision, not an AI guess. -->

- Renaming public APIs, exported symbols, routes, or DB columns.
- Adding a new top-level dependency.
- Changing build, lint, format, or CI configuration.
- Schema migrations (anything that touches production data shape).
- Anything that affects more than ~10 files at once.

## Testing rules

<!-- FILL: project-specific testing rules. Detailed guidance goes in
     skills/write-tests.md. -->

- New behavior needs a test. Bug fixes need a regression test.
- Don't mock the database in integration tests; use the test DB.
- Don't snapshot-test anything you wouldn't be willing to read on every PR.

## Security baseline

- Validate input at trust boundaries (HTTP handlers, queue consumers, file
  uploads). Trust internal code.
- Parameterize all SQL. No string concatenation into queries.
- Escape output by default. Opt _out_ of escaping deliberately, never by
  accident.

## When in doubt

If a rule here conflicts with what the code is actually doing, **trust the
code and flag the conflict**. The rules file may be stale; the running code
is authoritative.
