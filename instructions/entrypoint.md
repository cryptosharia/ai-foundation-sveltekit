# CryptoSharia SvelteKit AI Rules

This is the rule entrypoint for CryptoSharia SvelteKit app repositories.

## Rule Priority

1. User instructions
2. Project-local rules in the current repository
3. `<ai-rules>/entrypoint.md`
4. Other files in `<ai-rules>/`
5. Default assistant behavior

## Core Operating Model

- Default flow: inspect -> decide -> implement -> verify -> report.
- Do not ask for confirmation for low-risk tasks.
- Ask only for destructive actions, unclear high-impact contract/security changes, or missing secrets/credentials.
- For scoped features/refactors that need planning artifacts, follow `<ai-rules>/planning.md`.

## AI Rules (Canonical Modules) vs AI Skills (Playbooks)

- Treat `<ai-rules>/*` as AI Rules (Canonical Modules): policy, gates, invariants, and shared context.
- Treat `<ai-skills>/*` as AI Skills (Playbooks) for task execution.
- AI Skills (Playbooks) may reference AI Rules (Canonical Modules) and include local `references/` for workflow-specific detail.
- Keep shared checklists and non-negotiables in AI Rules (Canonical Modules) to avoid drift.

## Governance Updates

- Apply user feedback immediately for the current session.
- If a governance change would be reasonable and durable, propose a persistent update to `<ai-rules>/*` or `<ai-skills>/*`.
- Do not edit governance files silently; require explicit user confirmation (for example: `codify`) before persistent updates.
- Codify only stable, cross-project preferences; keep one-off preferences session-scoped.

## Non-Negotiables

- Security > speed.
- Do not expose secrets in browser-visible code or `PUBLIC_` environment variables.
- Keep privileged upstream calls in server-only SvelteKit surfaces (BFF pattern).
- Do not weaken auth, authorization, trust-boundary, or data exposure protections.
- Do not change public contracts silently.

## Required Verification

- Run project verification commands (`check`, `lint`, `test`) for non-trivial changes.
- Keep BFF runtime behavior aligned with documented contracts.
- If checks cannot run, report exactly what is blocked and what to run manually.

## AI Rule Modules

- `<ai-rules>/cryptosharia-context.md` - business, product, and ecosystem context.
- `<ai-rules>/security-audit.md` - security checklist before finalization.
- `<ai-rules>/bff-pattern.md` - BFF boundaries, secret handling, and response/caching rules.
- `<ai-rules>/conventions.md` - TypeScript/Svelte/SvelteKit coding conventions.
- `<ai-rules>/planning.md` - planning policy, approval gate, and escalation rules.
- `<ai-rules>/mcp-svelte.md` - Svelte MCP usage and Svelte 5 conventions.
