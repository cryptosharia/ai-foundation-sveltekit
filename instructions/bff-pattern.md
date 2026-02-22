# BFF Pattern Rules

These rules codify the Backend-for-Frontend (BFF) pattern.

## Decision Rubric

- SHOULD call an upstream service directly from the browser only when ALL are true:
  - the upstream endpoint is public (no API keys, no session cookies, no OAuth tokens)
  - the data is non-sensitive
  - the upstream contract is already suitable for the UI (no reshaping/aggregation needed)
  - CORS, rate limits, and performance are acceptable
- MUST use a BFF layer when ANY are true:
  - a secret is required (API key, client secret, service token)
  - authentication/authorization is required
  - the data is sensitive (PII, financial, internal identifiers, privileged metadata)
  - the UI needs aggregation, normalization, filtering, sorting, or pagination policy
  - you need consistent error mapping, caching rules, or rate-limit shielding

## Secret Handling

- NEVER read secrets in browser code.
- NEVER read secrets in universal modules that can execute on the client (e.g. `+page.ts`, `+layout.ts`, shared `$lib` used by components).
- MUST read secrets only in server-only modules. SvelteKit server-only surfaces include:
  - API routes (`src/routes/**/+server.ts`)
  - Server load functions (`src/routes/**/+page.server.ts`, `src/routes/**/+layout.server.ts`)
  - Form actions (`export const actions` in `src/routes/**/+page.server.ts`)
  - Remote functions (`src/lib/**/*.remote.ts`)
- MUST source secrets from `$env/static/private` (or `$env/dynamic/private` when truly needed).
- Config values like upstream base URLs are often safe to expose as public env (e.g. `PUBLIC_UPSTREAM_BASE_URL` via `$env/static/public`), but keep them private if they reveal internal topology or are only reachable from the server.
- MUST NOT pass secrets to the client (no response bodies, no headers, no serialized load data).

## Boundary and Contract Rules

- BFF endpoints MUST expose a frontend-shaped contract:
  - stable response shape and naming
  - minimal fields needed by the UI
  - no accidental passthrough of upstream internals
- SHOULD normalize/validate upstream data before returning it to the UI.
- MUST keep upstream-specific details behind the boundary (header names, error schemas, pagination quirks, field names).
- SHOULD define explicit TypeScript types for the BFF response payloads (these types belong to the BFF contract, not the upstream).

## SvelteKit Placement Rules

- Privileged upstream calls MUST happen server-side:
  - BFF API routes (`src/routes/**/+server.ts`)
  - Server load functions (`src/routes/**/+page.server.ts`, `src/routes/**/+layout.server.ts`)
  - Form actions (`export const actions` in `src/routes/**/+page.server.ts`)
  - Remote functions (`src/lib/**/*.remote.ts`)
- Browser-visible surfaces MUST call the BFF (not privileged upstreams):
  - Components (`src/**/*.svelte`)
  - Universal load functions (`src/routes/**/+page.ts`, `src/routes/**/+layout.ts`)
- SHOULD use SvelteKit-provided `fetch` inside server contexts.
  - Reason: consistent cookies/credentials behavior in SSR and ability to call internal routes efficiently.

## Error Handling Rules

- BFF MUST map upstream failures to UI-safe errors:
  - return an appropriate HTTP status code
  - return a minimal error payload intended for the UI (message + optional error code)
- MUST NOT forward upstream error bodies verbatim if they might include sensitive details.
- SHOULD keep error shapes consistent across BFF routes.

## Caching Rules

- Sensitive or authenticated responses MUST set `cache-control: no-store`.
- Non-sensitive responses MUST set an explicit cache policy (avoid relying on implicit defaults).
- If returning user-specific content, MUST ensure shared caches cannot store it.

## Observability Rules

- SHOULD include a correlation/request ID in server logs and pass it to upstream services when possible.
- MUST NOT log secrets.
