---
name: cryptosharia-security-audit
description: Run BFF and frontend security checks before finalizing changes
---

# CryptoSharia Security Audit

## When to use

Use this skill before finalizing work that touches auth/session, server routes, upstream integration, user data, caching, or error handling.

## Source of truth

- `<ai-rules>/security-audit.md`
- `<ai-rules>/bff-pattern.md`
- `<ai-rules>/entrypoint.md`

## Local references

- `references/audit-report-template.md`

## Workflow

1. Review changed files with BFF boundary lens
2. Execute checklist from Security Audit module
3. Fix critical/high findings before final verification
4. Run check/lint/test project gates
5. Produce final security report using template

## Done definition

- Findings are documented with path, risk, and fix
- Deferred risks are explicit
- Verification gate status is reported clearly
