# CryptoSharia SvelteKit AI Skills

This directory contains reusable AI Skills (Playbooks) for CryptoSharia SvelteKit app repositories.

## Skill Folder Layout

```text
<skill-name>/
  SKILL.md                 # required entrypoint
  references/*.md          # optional templates/examples/checklists
```

## Available Skills

| Skill                          | Use for                                                                   |
| ------------------------------ | ------------------------------------------------------------------------- |
| `cryptosharia-api-integration` | Integrating SvelteKit apps with CryptoSharia API using BFF-safe placement |
| `cryptosharia-planning-pack`   | Creating planning packs (`spec.md` + `tasks.md`) with approval gate       |
| `cryptosharia-security-audit`  | Running security checks and producing audit reports before finalization   |

## Suggested Skill Chains

- New integration flow: `cryptosharia-planning-pack` -> `cryptosharia-api-integration` -> `cryptosharia-security-audit`
- Sensitive/BFF-heavy change: `cryptosharia-planning-pack` -> `cryptosharia-api-integration` -> `cryptosharia-security-audit`

## Notes

- Keep shared policies in AI Rules (Canonical Modules), not duplicated in every skill.
- Keep skill guidance procedural and task-focused.
