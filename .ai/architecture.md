# Architecture

> Loaded on demand — only when the agent is doing structural work. Length is
> fine here; correctness matters more than brevity.

## One-paragraph overview

<!-- FILL: how the system fits together at a high level. A new engineer should
     be able to read this paragraph and roughly point at the right place for
     any change. -->

_Example: A Next.js app serves the UI and JSON API routes; API routes call
into a service layer in `src/server/`, which talks to Postgres via Prisma and
to Stripe via their SDK. Background reconciliation jobs run via Inngest, with
job definitions in `src/server/jobs/`. There is no separate backend service —
everything ships as one Next.js deployment._

## Components

<!-- FILL: list the major components. For each: where the code lives, what
     it's responsible for, and what it explicitly is NOT responsible for. -->

### `<Component name>`

- **Lives in:** <!-- e.g. src/server/reconciliation/ -->
- **Responsible for:** <!-- one-line summary of its job -->
- **Not responsible for:** <!-- things callers commonly assume it does but it
  doesn't — these are the most useful lines in this whole doc -->
- **Key files:** <!-- 2–5 entry-point files inside the component -->

<!-- repeat per component -->

## Data model

<!-- FILL: describe the core entities and how they relate. Don't restate the
     schema — link to it. Focus on the conceptual model and any non-obvious
     invariants. -->

- **Source of truth:** <!-- e.g. prisma/schema.prisma -->
- **Core entities:** <!-- e.g. Org → User → Workspace → Project -->
- **Invariants worth knowing:**
  - <!-- e.g. A User belongs to exactly one Org. There is no cross-org access. -->
  - <!-- e.g. Soft-deletes use deletedAt; queries must filter it. -->

## Request lifecycle

<!-- FILL: trace one typical request end-to-end. Concrete > abstract. -->

_Example for a POST /api/orders request:_

1. `src/app/api/orders/route.ts` validates the body with a Zod schema.
2. Calls `createOrder` in `src/server/orders/service.ts`.
3. Service writes via `prisma.order.create` inside a transaction.
4. On commit, enqueues an `order.created` Inngest event.
5. Returns the order ID; the client subscribes to status via SSE on `/api/orders/:id/stream`.

## External integrations

<!-- FILL: third-party services. For each: what it's used for, where the
     client lives, and any quirks (rate limits, eventual consistency, etc.). -->

| Service | Used for | Client lives in | Quirks |
| ------- | -------- | --------------- | ------ |
| <!-- e.g. Stripe --> | <!-- payments --> | <!-- src/server/stripe/ --> | <!-- webhooks are eventually consistent; don't read-after-write --> |

## What's intentionally simple

<!-- FILL: choices that look naive but were deliberate. These are the things
     agents most often "fix" when they shouldn't. -->

- _Example: We don't have a service layer for read endpoints — they call
  Prisma directly in the route handler. Adding indirection here was rejected
  in [ADR-0003](decisions/0003-no-read-service-layer.md)._

## Where to look for more

- Per-decision context → [`decisions/`](decisions/)
- Domain terms → [`glossary.md`](glossary.md)
- How specific tasks get done → [`skills/`](skills/)
