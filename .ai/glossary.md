# Glossary

> Loaded on demand. Project-specific or domain-specific terms an agent would
> otherwise guess at (and guess wrong). Skip generic engineering terms.

> Format: bold term, then a single-sentence definition. If a term is used
> ambiguously in the codebase, say which usage means what.

<!-- FILL: replace these examples with real terms from your project.
     Aim for 10–40 entries — the things that come up in PRs and would confuse
     a new hire. -->

- **Payout** — Stripe's term for money moved from your Stripe balance into
  your bank account. Distinct from a _charge_ (incoming) or a _transfer_
  (between Stripe accounts).

- **Reconciliation** — In this codebase, matching a Stripe payout against
  the underlying orders that funded it. Not the same as accounting
  reconciliation (which is bookkeeper-facing).

- **Workspace** — A tenant. Each customer has one workspace; users belong to
  workspaces, not directly to the app.

- **Job** — A background task run by Inngest. Always defined in
  `src/server/jobs/`. Not to be confused with a "task" (UI concept — a
  user-facing checklist item).

- **Soft delete** — Setting `deletedAt` rather than removing the row. All
  list queries must filter `deletedAt IS NULL`; we have a Prisma middleware
  that does this for most models but not all (see [`architecture.md`](architecture.md)).

<!-- Add terms in alphabetical order. -->

## Acronyms

<!-- FILL: project acronyms. -->

- **<!-- ACME -->** — <!-- expansion + what it means in our context -->
