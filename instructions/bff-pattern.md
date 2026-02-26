# BFF Pattern Invariants

These are stable architecture rules for CryptoSharia SvelteKit apps using Backend-for-Frontend (BFF) boundaries.

## 1) Decision Rubric

Use direct browser-to-upstream calls only when all are true:

- Upstream endpoint is fully public (no secrets/session/auth required).
- Data is non-sensitive.
- Contract already fits UI needs without transformation.
- CORS, rate limits, and performance are acceptable.

Use BFF boundary when any are true:

- A secret is required (`Api-Key`, service token, client secret).
- Auth/authorization/ownership checks are required.
- Data is sensitive (PII, internal identifiers, privileged metadata).
- UI needs normalization, aggregation, filtering, or policy-driven pagination.
- Consistent error mapping/caching/rate-limit shielding is needed.

## 2) Secret Handling

- Never read secrets in browser-visible code.
- Never read secrets in universal modules that can execute client-side.
- Read secrets only in server-only surfaces/modules.
- Never pass secrets to client responses, serialized load data, or client headers.

## 3) Server-Only Surfaces

Privileged upstream calls are allowed only in:

- `src/routes/**/+server.ts`
- `src/routes/**/+page.server.ts`
- `src/routes/**/+layout.server.ts`
- `src/lib/**/*.remote.ts`

## 4) Browser-Visible Surfaces

Browser-visible code must call internal BFF endpoints for protected data:

- `src/**/*.svelte`
- `src/routes/**/+page.ts`
- `src/routes/**/+layout.ts`

No protected upstream calls or secret-bearing headers in these surfaces.

## 5) Contract and Response Discipline

- BFF responses are UI-shaped, minimal, and stable.
- Upstream quirks stay behind the BFF boundary.
- Validate/normalize upstream responses before returning to UI.
- Error responses are UI-safe and consistent.

## 6) Auth and Error Semantics

- Use explicit auth/ownership checks when required.
- Keep status semantics consistent (`401` unauthenticated, `403` forbidden).
- Do not forward raw upstream error bodies if they may leak internal details.

## 7) Caching and Observability

- Sensitive/authenticated responses use `cache-control: no-store`.
- Non-sensitive responses use explicit cache policy.
- Logs should include useful correlation data without secrets/PII leakage.
