---
name: cryptosharia-api-integration
description: Standard way to integrate SvelteKit apps with CryptoSharia API (typegen + client + BFF-safe placement)
---

# CryptoSharia API Integration

## When to use

Use this skill when implementing or updating API calls from CryptoSharia SvelteKit apps.

## Source of truth

- `<ai-rules>/bff-pattern.md`
- `<ai-rules>/security-audit.md`

## Local references

- `references/examples.md`

## Prerequisites

- Required environment variables are configured in server/client scopes correctly.
- Protected API keys/secrets remain server-only.

## Workflow

1. Generate API contract types

```sh
npm run gen:api-types:preview
npm run gen:api-types:prod
```

Expected output: app-local generated API types file.

2. Choose correct SvelteKit surface

- Browser-visible surfaces: public endpoints only (no protected headers/secrets).
- Server-only surfaces: protected endpoints allowed.

3. Use shared client factories/helpers

- Use public client for public upstream calls.
- Use server client for protected upstream calls.

4. Keep BFF contract clean

- Return UI-safe, minimal payloads.
- Map/sanitize upstream errors before returning to UI.
- Set explicit cache policy (`no-store` for sensitive/user-specific responses).

5. Verify

- Run check/lint/test project gates.

## Done definition

- No secrets leaked into browser-visible surfaces.
- Placement follows BFF pattern boundaries.
- Error/caching behavior is explicit and safe.
- Verification gates pass (or blockers are reported clearly).
