# Architecture Decision Records (ADRs)

Short, dated records of architectural choices and **why** they were made.
Useful when an agent (or a future engineer) is tempted to "fix" something
that looks odd but was deliberate.

## Conventions

- One file per decision: `NNNN-short-title.md` (e.g. `0001-use-prisma.md`).
- Numbered in order of acceptance. Numbers never get reused.
- Once a decision is **accepted**, treat the file as immutable. To change
  course, write a new ADR that supersedes the old one and update the old
  one's status header to reference the new one.

## When to write an ADR

You probably want one if:

- The choice is hard to reverse (database, framework, deployment target).
- A reasonable engineer would make the opposite choice and you need to
  document why you didn't.
- Future you / a new hire / an AI agent would otherwise undo the decision
  thinking it was an oversight.

You probably **don't** need one for:

- Routine library picks with cheap reversal cost.
- Decisions already captured in code comments or the type system.
- "We use Postgres" — that lives in [`../project.md`](../project.md).

## Template

Copy [`TEMPLATE.md`](TEMPLATE.md) to start a new ADR.

## Index

<!-- FILL: list ADRs as you add them. Format:
-->
<!-- - [0001](0001-example.md) — One-line summary -->
