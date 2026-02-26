# Security Audit Checklist

Run this checklist before finalizing work that touches auth/session, BFF routes, upstream integrations, user data, DB writes, caching, or API responses.

## 1) Secrets and Environment Safety

- No secrets in committed files (`.env`, credential files, token dumps).
- No secrets in browser-visible code (`.svelte`, `+page.ts`, `+layout.ts`, client `$lib` modules).
- No secrets in `PUBLIC_` environment variables.
- Server-only secrets are read only from server-only surfaces/modules.

## 2) BFF Boundary and Privileged Calls

- Privileged upstream calls happen only in server-only SvelteKit surfaces.
- Browser-visible surfaces call internal BFF endpoints for protected data.
- `Api-Key` or equivalent secrets are never attached in browser-visible requests.
- Upstream provider quirks stay behind BFF boundaries (headers, error shapes, field quirks).

## 3) Auth and Authorization

- Authentication checks are explicit on protected routes/actions.
- Authorization and ownership checks are explicit where required.
- Status semantics are consistent (`401` unauthenticated, `403` forbidden).
- Session-sensitive operations use defensive defaults (`no-store`, minimal exposure).

## 4) Input and Write Safety

- Untrusted input is validated before use.
- No mass assignment from request payloads into writes.
- Allowed fields are explicitly picked for create/update.
- SQL/ORM access uses parameterized APIs (no raw unsafe string SQL).

## 5) Data Exposure and Error Handling

- Responses do not expose sensitive fields (hashes, refresh tokens, private metadata).
- Upstream error bodies are sanitized before returning to clients.
- Internal exception details are not leaked to users.
- Response payloads are intentionally shaped for UI needs.

## 6) Caching and Logging

- Sensitive/user-specific responses set `cache-control: no-store`.
- Non-sensitive responses have explicit cache policy.
- Logs avoid secrets and unnecessary PII.
- If correlation IDs are used, they do not carry sensitive payload content.

## 7) Type Safety and Verification

- Avoid `any` for untrusted inputs; use `unknown` with narrowing.
- Add regression tests for security-sensitive fixes.
- Final gates: `npm run check`, `npm run lint`, `npm test` (or project-equivalent scripts).

## Audit Report Format

- Findings: `<none>` or bullet list with `path`, `risk`, and `fix`.
- Residual risk: explicit statement if anything is intentionally deferred.
