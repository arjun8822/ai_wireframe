# Project

> Fill in the placeholders. Keep this file **short** (under ~150 lines) — it's
> loaded into the agent's context on every turn.

## What this project is

<!-- FILL: 2–4 sentences. What is the product/library/service? Who uses it?
     What problem does it solve? Skip the marketing copy — the agent needs
     enough to make sensible suggestions, not a pitch. -->

_Example: A web app that lets small e-commerce teams reconcile their Stripe
payouts against their order data. The primary users are bookkeepers at
companies doing $1M–$50M annual revenue._

## Stack

<!-- FILL: list the major technologies. Versions matter — the agent will
     otherwise hallucinate API shapes from training data. -->

- **Language(s):** <!-- e.g. TypeScript 5.4, Python 3.12 -->
- **Framework(s):** <!-- e.g. Next.js 15 (App Router), FastAPI -->
- **Database:** <!-- e.g. Postgres 16 via Prisma -->
- **Test framework:** <!-- e.g. Vitest, pytest -->
- **Lint / format:** <!-- e.g. Biome, ruff + black -->
- **Package manager:** <!-- e.g. pnpm, uv -->
- **Other:** <!-- queues, caches, infra tools that matter -->

## Run / test / build

<!-- FILL: the exact commands. The agent will use these — wrong commands
     waste turns. -->

```bash
# Install dependencies
<!-- e.g. pnpm install -->

# Run the dev server
<!-- e.g. pnpm dev -->

# Run tests
<!-- e.g. pnpm test -->

# Run a single test file
<!-- e.g. pnpm test path/to/file.test.ts -->

# Lint
<!-- e.g. pnpm lint -->

# Typecheck
<!-- e.g. pnpm typecheck -->

# Build for production
<!-- e.g. pnpm build -->
```

## Entry points

<!-- FILL: where to start reading. Point at the files an agent should open
     first to understand the shape of the codebase. -->

- **App entry:** <!-- e.g. src/app/layout.tsx -->
- **API routes:** <!-- e.g. src/app/api/ -->
- **Data layer:** <!-- e.g. src/db/ with Prisma schema at prisma/schema.prisma -->
- **Domain logic:** <!-- e.g. src/lib/reconciliation/ -->
- **Tests:** <!-- e.g. co-located *.test.ts files -->

## Environments

<!-- FILL: only if the agent needs to know about envs to suggest the right
     things. Otherwise delete. -->

- **Local:** <!-- e.g. uses a Docker postgres, .env.local for secrets -->
- **Staging:** <!-- e.g. branch deploys on Vercel preview URLs -->
- **Production:** <!-- e.g. main branch auto-deploys to vercel.com -->

## What's _not_ in this repo

<!-- FILL (optional but useful): things an agent might assume are here but
     aren't, so it doesn't go hunting. -->

- _Example: the mobile app lives in a separate repo (`acme/mobile`)._
- _Example: shared design tokens come from the `@acme/tokens` package._

## Where to look next

- Architecture and data flow → [`architecture.md`](architecture.md)
- Coding rules → [`rules.md`](rules.md)
- Code style and naming → [`style.md`](style.md)
- Domain terms → [`glossary.md`](glossary.md)
- Common workflows → [`skills/`](skills/)
