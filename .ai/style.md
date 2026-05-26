# Style Guide

> Loaded on demand. Use this for project-specific style rules that the
> formatter/linter doesn't already enforce — anything the formatter handles
> doesn't need to be repeated here.

## Naming

<!-- FILL: project conventions for names. Examples: -->

- **Files:** <!-- e.g. kebab-case.ts for modules, PascalCase.tsx for components -->
- **Variables / functions:** <!-- e.g. camelCase; verbs for functions, nouns for variables -->
- **Types / classes:** <!-- e.g. PascalCase; no "I" prefix for interfaces -->
- **Constants:** <!-- e.g. SCREAMING_SNAKE_CASE only for top-level immutables -->
- **Booleans:** <!-- e.g. prefix with is/has/can/should -->
- **Async functions:** <!-- e.g. no async suffix; the return type already says so -->

## Functions

<!-- FILL: shape and size rules. -->

- Keep functions short — if you need section-header comments inside one, it's
  two functions.
- Prefer pure functions where possible; isolate I/O at the edges.
- Return early; avoid deep nesting. No `else` after `return`.
- A function with more than ~4 parameters should take an options object.

## Errors

<!-- FILL: error-handling conventions. This is the area agents get wrong
     most often when given no guidance. -->

- Don't catch errors you can't meaningfully handle. Let them propagate.
- Don't catch + re-throw without adding context. If you catch, add info.
- Don't wrap successful return values in `try`. Wrap only the call that can
  fail.
- For user-facing errors, throw a typed error class — don't return error
  strings from successful-looking returns.

## Comments

<!-- These are good defaults — keep, edit, or replace. -->

Default: write no comment.

Add a comment only when the **why** is non-obvious:

- A hidden constraint a reader can't see from the code (`// Stripe requires
  amounts in cents`).
- A workaround for a specific bug (`// Workaround for next/router bug #58293,
  remove after upgrading past 14.2.5`).
- A subtle invariant that future edits could break.

Don't write:

- Comments that restate the code (`// loop over users`).
- Comments naming the caller or task (`// for the checkout flow`,
  `// added in JIRA-1234`) — that belongs in the commit/PR.
- Block-comment "headers" inside a function. Extract a function instead.

Docstrings: one short line for public exports. Skip docstrings on internal
helpers with self-evident names.

## Imports

<!-- FILL: project import conventions. -->

- Order: stdlib → third-party → first-party → relative. (Or whatever the
  formatter does — don't fight it.)
- Use the path alias for cross-module imports (e.g. `~/lib/x`), not deep
  relative paths (`../../../lib/x`).
- No barrel `index.ts` files unless they already exist. Import the source
  module directly.

## Tests

<!-- FILL: project-specific test style. Detailed workflow goes in
     skills/write-tests.md. -->

- One assertion per test where reasonable. If a test needs setup + 5
  assertions, it's probably testing too much.
- Test names describe behavior in plain English: `it("returns 401 when the
  token is expired")`.
- Use real values, not fixtures, when the value fits on one line.
- Mock at the boundary (network, filesystem, clock). Don't mock your own
  code.

## Forbidden patterns

<!-- FILL: things that look fine to a generic AI but are wrong for your
     project. The most valuable section of this file. -->

- _Example: don't use `lodash`; the codebase migrated off it. Use stdlib
  equivalents or the helpers in `src/lib/util.ts`._
- _Example: don't add `useEffect` for derived state — derive it during
  render._
- _Example: don't introduce a new ORM call from a React component; data
  access goes through `src/server/`._
