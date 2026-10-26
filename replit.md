# FinsightCalc

Free worldwide calculators with transparent formulas, useful examples, and browser-local calculations.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/free-calculators/src/calculators.ts` — published calculator registry, formulas, validation, examples, and page content.
- `artifacts/free-calculators/src/Site.tsx` — routes, navigation, calculator forms, and informational pages.
- `artifacts/free-calculators/scripts/generate-sitemap.mjs` — generates sitemap and robots files using the configured canonical origin.
- `artifacts/free-calculators/src/calculators.test.ts` — unit tests for calculator formulas and input boundaries.

## Architecture decisions

- Basic calculations run in the browser; no account or database is needed for the current tools.
- Keep unverified tax rules and live market rates unpublished rather than substituting invented or stale values.
- `VITE_CANONICAL_ORIGIN` remains unset until the supplied domain resolves; the contact page uses the email supplied by the user.

## Product

The current release includes 20 calculators spanning finance, loans, education, everyday math, health, home, science, and conversions. Each has a dedicated page with instructions, formula notes, an example, limitations, FAQs, and related links. Run `pnpm --filter @workspace/free-calculators run test:calculators` for calculator logic tests.

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
