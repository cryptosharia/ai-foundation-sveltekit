# Coding Conventions

These conventions apply across CryptoSharia SvelteKit app repositories unless project-local rules override them.

## TypeScript

- Prefer strict TypeScript settings.
- Avoid `any`; use `unknown` with narrowing for untrusted inputs.
- Prefer `type` over `interface` for most app-level type definitions.
- Keep runtime validation explicit at boundaries (forms, route handlers, upstream responses).

## Svelte and SvelteKit

- Keep privileged logic in server-only surfaces (`+server.ts`, `+page.server.ts`, `+layout.server.ts`, actions, `.remote.ts`).
- Keep browser-visible logic free from secrets and protected upstream access.
- Use small, composable components and avoid large mixed-responsibility files.
- Keep load/action/route handler logic explicit and readable.

## Formatting and Linting

- Follow each repository's Prettier and ESLint configuration as source of truth.
- Do not hardcode style assumptions when local project config differs.
- Resolve lint/type issues instead of suppressing them unless there is clear justification.

## Import Conventions

- Prefer `$lib` aliases for internal imports where configured.
- Import ordering (default):
  1. External packages
  2. Internal aliases (`$lib`, app-local aliases)
  3. Relative imports

## Naming Conventions

| Type                   | Convention       | Example                     |
| ---------------------- | ---------------- | --------------------------- |
| Components             | PascalCase       | `UserCard.svelte`           |
| Functions/variables    | camelCase        | `handleSubmit`, `isLoading` |
| Constants              | UPPER_SNAKE_CASE | `MAX_RETRIES`               |
| Files (non-components) | kebab-case       | `api-client.ts`             |
| Types                  | PascalCase       | `UserProfileResponse`       |

## Error Handling

- Handle async operations explicitly (`try/catch` where appropriate).
- Return UI-safe error shapes from BFF endpoints.
- Do not leak internal stack traces or provider internals.

## Styling

- Follow the app's existing design system and styling approach.
- Prefer consistency with local project patterns over introducing new style systems.
- If Tailwind is used, keep utility usage intentional and readable.

## Testing

- Prefer Vitest for unit/integration testing where available.
- Name tests consistently (`*.test.ts` or project-local standard).
- Add tests for behavior changes, especially auth/security/BFF boundary changes.
