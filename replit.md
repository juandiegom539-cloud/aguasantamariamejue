# Agua Santa María Mejue

Página informativa y catálogo de compra para Agua Santa María Mejue, con pedidos directos por WhatsApp y cobertura en Toledo, Norte de Santander.

## Run & Operate

- `pnpm --filter @workspace/agua-santa-maria-mejue run dev` — run the storefront
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

- `artifacts/agua-santa-maria-mejue/src/App.tsx` — single-page storefront, catalog, quantity controls, and WhatsApp links
- `artifacts/agua-santa-maria-mejue/src/index.css` — storefront theme, responsive layout, motion, and accessibility styles
- `artifacts/agua-santa-maria-mejue/public/assets/` — product photography supplied for the site

## Architecture decisions

- The storefront is frontend-only because purchase requests are sent directly to WhatsApp.
- Product ordering uses prefilled `wa.me` links so customers can choose a product and quantity without an account or checkout system.
- Catalog prices are shown in Colombian pesos: $9.000 for the 20-unit small-bag package, $10.000 for the 5-gallon botellón, and $3.500 for the 6-liter large bag.
- Authentication uses Replit-managed Clerk with browser sessions and a server-side Clerk proxy for production.

## Product

- Responsive Spanish landing page for Agua Santa María Mejue.
- Catalog for small bags in packs of six, 5-gallon botellones, and 6-liter large bags.
- Direct ordering through WhatsApp at `573126672205`.
- User sign-up, sign-in, and sign-out with Clerk, including branded auth screens.
- Support contact through `juandiegom539@gmail.com`.
- Delivery coverage is limited to Toledo, Norte de Santander.

## User preferences

- Keep catalog prices easy to edit in the product data when the business updates them.

## Gotchas

- The web artifact workflow supplies `PORT` and `BASE_PATH`; run the artifact through its managed workflow rather than starting Vite manually.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
