# AI Foundation Repo Rules

This file applies when working inside the `cryptosharia/ai-foundation` repository.

This repository is the shared OpenCode AI foundation used by multiple CryptoSharia projects.

## Non-Negotiable

- Treat changes here as production-impacting (they affect assistant behavior across many repos).
- Do not introduce secrets or private environment values.
- Keep changes small, reviewable, and easy to revert.

## Change Process

- If you add/remove instruction modules under `instructions/`, update `manifest.json`.
- If you change rules that affect security/auth/data exposure, call out the impact explicitly.
