# MarketPulse

MarketPulse is a polished digital marketing campaign management and analytics workspace for planning campaigns, understanding audiences, and turning channel data into clear next steps.

## Run & Operate

- `pnpm --filter @workspace/marketpulse run dev` — run the MarketPulse frontend
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)

The MarketPulse prototype intentionally uses browser localStorage and does not require the API server or a database.

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/marketpulse/src/App.tsx` — app shell, routes, seeded demo data, localStorage state, and page components
- `artifacts/marketpulse/src/index.css` — MarketPulse theme tokens, responsive layout, and motion styles
- `artifacts/marketpulse/.replit-artifact/artifact.toml` — artifact service and preview routing
- `lib/api-spec/` and `artifacts/api-server/` — shared workspace backend scaffold, not used by the MarketPulse prototype

## Architecture decisions

- MarketPulse is frontend-only for the internship prototype; data persistence is scoped to the current browser through localStorage.
- Demo data is seeded on first load so every analytics surface has meaningful content without a backend.
- The app uses wouter routes with a shared shell and keeps campaign CRUD in client state so create/edit/delete flows are immediate and demonstrable.
- Browser print is the report export path instead of a server-side PDF dependency.

## Product

The prototype includes login/demo entry, an executive dashboard, campaign CRUD and detail views, analytics, campaign health scoring, audience insights, content performance, SEO analytics, a campaign calendar, rule-based marketing insights, theme switching, responsive navigation, and a printable report.

## User preferences

No durable preferences recorded.

## Gotchas

- Demo login is intentionally local and has no authentication backend.
- Campaign, theme, and demo session state are browser-local; clearing site storage resets the prototype to seeded data.
- The report's Download action uses the browser print dialog, where the user can choose Save to PDF.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
