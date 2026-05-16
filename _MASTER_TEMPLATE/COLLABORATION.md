# COLLABORATION.md

Rules for multiple humans and AI harnesses working in the same repo.

## Principle

Work must be easy to resume, review, and undo. Shared-state actions require explicit approval.

## Session Startup

Before editing, every collaborator or AI harness should check:

```sh
git status
git branch --show-current
git log --oneline -5
```

Then read:

- `AGENTS.md`
- `README.md`
- `PROJECT_STATE.md`
- `RULES.md`
- `PROCESS.md`
- `TASKS.md` when active work exists
- `DECISIONS.md` when decisions, exceptions, APIs, architecture, or product direction matter

## Branch Rules

- Use a separate branch for non-trivial work.
- Prefer branch names like `codex/<task-name>` or `<name>/<task-name>`.
- Do not push directly to `main` unless the repo owner explicitly approves it.
- Pull or fetch current `main` before starting work when practical.
- Avoid editing the same files as another active task unless coordination is explicit.

## Approval Levels

Normal work approval allows scoped edits on a branch.

Example:

```text
Approved: work on task "add DB inspection scripts" on a new branch.
```

Production or shared-state approval must name the action and scope.

Valid examples:

```text
Approved: push current committed changes to main.
Approved: deploy production.
Approved: delete smoke rows from production database only.
Approved: update the production webhook URL.
```

Invalid for production or shared-state actions:

```text
go
continue
do it
ship it
```

For normal coding, short approvals like `go` or `continue` are acceptable.

## Shared-State Safety

Ask for explicit approval before:

- pushing to `main`
- deploying production
- changing production environment variables
- changing webhooks, domains, cron jobs, or public endpoints
- running destructive database changes
- deleting or backfilling production data
- rotating secrets or credentials
- making paid or high-volume external API calls

## Secrets And Private Data

- Do not expose, print, commit, or summarize secrets.
- Do not commit `.env`, `.env.local`, `.vercel`, credentials, tokens, private chat IDs, or private message content.
- Keep secrets out of logs, screenshots, final responses, and handoff notes.
- If private identifiers are needed for debugging, use redacted forms.

## Task Ownership

Before editing, state or record:

```text
Task:
Branch:
Files likely touched:
Production impact:
Database impact:
Verification plan:
```

If multiple collaborators are active, avoid overlapping ownership unless the overlap is agreed.

## Verification

- Run the relevant verification before handoff when possible.
- State exactly what passed, failed, or was not run.
- Tests should mock external providers by default.
- Live external checks must be labeled as live and should respect rate limits.

## Handoff Format

Use this format when pausing, finishing, or handing work to another collaborator:

```text
Status:
Branch:
Files changed:
Database/prod impact:
Verification:
Next recommended task:
Known risks:
```

Also update `PROJECT_STATE.md` after meaningful work.

## Commits And PRs

- Commit small, coherent units of work.
- Include docs/state updates in the same branch when behavior or workflow changes.
- Prefer PR review before merging shared work.
- Direct `main` pushes require explicit owner approval.
