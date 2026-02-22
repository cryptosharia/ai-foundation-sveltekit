# CryptoSharia Project AI Rules (Entrypoint)

These rules apply to the CryptoSharia project repository you are working in.

Additional authoritative rule modules may be loaded via your project's OpenCode config `instructions` setting.

## Precedence

- Project rules (in the repo you are working in) override any global/personal rules when they conflict.
- If modular rule files conflict with this entrypoint, this entrypoint file wins.

## Non-Negotiable Rules

- NEVER execute a plan or implement changes without explicit user approval ("yes", "go ahead", "proceed", etc.).
- Do not relax security/safety constraints without explicit user instruction.

## Collaboration Protocol

- Handshake protocol: research/plan -> propose -> wait for explicit approval -> execute.
- No hero assumptions: never run extra commands or follow-up changes unless explicitly approved.
- Security-first: for changes involving auth, secrets, caching, or data exposure, call out security impact.

## Communication

- Be concise by default.
- Prefer CryptoSharia-relevant examples when possible.

## Response Style and Token Efficiency

- Default to short, direct answers that address only the user's explicit question.
- Avoid unsolicited tangents, broad comparisons, or extra options unless requested.
- Expand only when the user explicitly asks (e.g., "expand", "deep dive", "more details", etc).
