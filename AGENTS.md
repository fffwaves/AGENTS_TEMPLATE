# Codex Global Instructions

Prefer the `codex` binary for Codex-managed coding sessions so Codex reads global config, `AGENTS.md`, project rules, and repository context correctly.

## Global Rules

- Follow the repository's own `AGENTS.md` when present.
- Do not proactively load project planning files unless the task requires them or the repo's `AGENTS.md` asks for them.
- For unfamiliar repos, start with lightweight inspection: `README.md`, package metadata, and targeted file search.
- Do not run destructive commands without explicit approval.
- Do not expose, print, commit, or summarize secrets.
- Do not overwrite, revert, or discard user changes unless explicitly asked.
- Keep changes scoped to the task and follow existing project conventions.
- Verify coding work before finishing when a concrete check is available.
- If the same deterministic failure happens twice, stop retrying and change approach.
- Repo-local `AGENTS.md` and `RULES.md` may add or specialize these rules, but must not weaken safety rules.

## Rule Placement

- Keep global `AGENTS.md` short.
- Put project-specific commands, stack, setup, and workflow in the project's own docs.
- Use repo-local `AGENTS.md` as a router to those docs, not as a full manual.