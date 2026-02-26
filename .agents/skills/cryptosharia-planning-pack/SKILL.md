---
name: cryptosharia-planning-pack
description: Create planning pack files (spec + tasks) for approval-gated implementation
---

# CryptoSharia Planning Pack (Foundation Repo)

## When to use

Use this skill when you need to create a planning pack for non-trivial work.

## Source of truth

- `.agents/rules/planning.md`
- `.agents/rules/entrypoint.md`

## References

- `references/template-pack.md`

## Workflow

1. Create `planning/<plan-name>/`
2. Add `spec.md` and `tasks.md` using the template pack
3. Ask for explicit approval before implementing
4. Execute using `tasks.md` allowed files + constraints

## Done definition

- Acceptance criteria in `spec.md` satisfied
- Verification commands in `spec.md` pass
- `tasks.md` updated with execution log and completion status
