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

## Permission Blocks

`Go` is valid only within the exact scope written in the block.

Short instructions like `go`, `continue`, or `work on it` mean normal branch work only. They never authorize production/shared-state work.

Use these copy-paste blocks when delegating work:

### Normal Branch Work

```text
Go: work on this as normal branch work only. You may edit files, run local tests, commit, and push the feature branch. Do not push to main, deploy, change production config, or delete production data.
```

### Commit Current Work

```text
Go: commit the current scoped changes on the current branch after verification passes. Do not push to main.
```

### Push Feature Branch

```text
Go: push the current feature branch to origin. Do not push to main.
```

### Open PR

```text
Go: open a PR from the current feature branch into main. Do not merge it.
```

### Production Read-Only Check

```text
Go: run production verification in read-only mode. You may inspect logs, webhook status, deployment status, and database rows. Do not change config, deploy, or delete data.
```

### Production Webhook Fix

```text
Go: check the production webhook. If it points to the wrong production URL, update only the webhook URL. Do not change env vars, database data, or code.
```

### Deployment Check

```text
Go: inspect the current production deployment and logs. Do not redeploy, promote, change env vars, or change project settings.
```

### Deploy Existing Main

```text
Go: deploy the current main branch to production. Do not change code, env vars, database data, or webhook settings unless I separately say so.
```

### Database Dry-Run Cleanup

```text
Go: inspect the production database and run cleanup dry-run only for the named bad rows. Do not delete anything.
```

### Database Actual Cleanup

```text
Go: delete only the named bad production database rows. Do not delete any other assets, reports, provider snapshots, command logs, or user data.
```

### Provider/API Live Smoke

```text
Go: run one live provider/API smoke test for the specified query only. Do not run loops, bulk checks, paid high-volume calls, or cleanup.
```

### Full Production Verification

```text
Go: run full production verification for the current deployment: webhook status, deployment status/logs, database read-only inspection, and one smoke flow. Do not delete data, change env vars, or deploy unless I separately say so.
```

### Main Push

```text
Go: push the current committed changes to main. Run verification first. Do not deploy, change production config, or delete production data unless I separately say so.
```

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
