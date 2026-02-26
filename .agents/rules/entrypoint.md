# AI Foundation Repo AI Rules

These rules apply when working inside `ai-foundation-sveltekit`.

This repo also exports cross-project guidance via `instructions/` + `manifest.json` for downstream apps.
The files under `.agents/` are for working on the foundation repo itself and are not intended to be exported.

## Rule Priority

1. User instructions
2. `.agents/rules/entrypoint.md`
3. Other files in `.agents/rules/`
4. Default assistant behavior

## Canonical Modules vs Skills

- Treat `.agents/rules/*` as canonical modules (policy, gates, invariants, shared context).
- Treat `.agents/skills/*` as procedures/playbooks.
- Skills may reference canonical modules; avoid duplicating global policy across multiple places.

## Governance Updates

- Apply user feedback immediately for the current session.
- If a governance change would be reasonable and durable, propose a persistent update.
- Do not edit governance files silently; require explicit user confirmation (for example: `codify`).

## Modules

- `.agents/rules/planning.md` - planning policy and approval gate
- `.agents/rules/cryptosharia-context.md` - company/ecosystem context for brainstorming
