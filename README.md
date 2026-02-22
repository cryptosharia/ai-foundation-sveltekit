# CryptoSharia AI Foundation

Shared OpenCode AI rules and skills for CryptoSharia projects.

## What this repo is

- A central place to maintain team-wide instructions (rules) and reusable skills.
- Consumed by projects via `@jgordijn/opencode-remote-config` (Git sync).

## How projects consume it

Each project includes a `.opencode/remote-config.json` that points at this repo and tracks `main`.

Example:

```json
{
	"installMethod": "copy",
	"repositories": [
		{
			"url": "https://github.com/cryptosharia/ai-foundation-sveltekit.git",
			"ref": "main",
			"instructions": "*",
			"skills": "*",
			"agents": "*",
			"commands": "*",
			"plugins": "*"
		}
	]
}
```

Notes:

- Tracking `main` means updates apply automatically on OpenCode startup.
- This example imports everything, including `instructions`, `skills`, `agents`, `commands`, and `plugins`.

## Repo structure

```
manifest.json
instructions/
skill/
agent/        (optional)
command/      (optional)
plugin/       (optional)
```

## Instructions

- `manifest.json` lists instruction markdown files that should be imported.
- Add new instruction modules under `instructions/` and remember to update `manifest.json`.
- Project entrypoint rules live in `instructions/entrypoint.md`.
- This repo's maintainer rules live in `AGENTS.md` (repo root) and are not imported into projects.

## Skills

- Skills live under `skill/<skill-name>/SKILL.md`.
- Any references should be within the same skill folder (e.g. `references/`).

## Change management

- Treat changes here as production-impacting (they affect how assistants behave across repos).
- Protect `main`, only commit to `main` once you're sure that the changes should be applied in production.
