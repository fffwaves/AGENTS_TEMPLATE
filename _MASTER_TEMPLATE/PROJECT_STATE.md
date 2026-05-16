# PROJECT_STATE.md

Current project continuity file. Update this after every completed task, fix, meaningful investigation, or interrupted work session.

## Current Status

- Status: planning
- Last updated: 2026-05-16
- Current focus: Template workflow setup
- Next step: Use `prompts/ai-dev-tasks/create-prd.md` for the first major feature PRD when scope is ready.

## Last Work

### 2026-05-16 - Added permission block wording

- Summary: Replaced approval-wording examples with reusable `Go:` permission blocks and clarified that short `go`/`continue` means normal branch work only, never production/shared-state work.
- Files touched: `COLLABORATION.md`, `PROJECT_STATE.md`
- Verification: content inspection
- Result: New projects can inherit clearer collaboration prompts without treating `Approved:` as a magic keyword.
- Resume from: specialize permission blocks inside project repos as needed.

### 2026-05-16 - Added collaboration and data architecture template docs

- Summary: Added generic multi-human/multi-agent collaboration rules, explicit approval gates for shared-state actions, handoff format, and data architecture guidance for storage, caching, analysis, and vector search.
- Files touched: `COLLABORATION.md`, `DATA_ARCHITECTURE.md`, `AGENTS.md`, `PROCESS.md`, `README.md`, `DECISIONS.md`, `PROJECT_STATE.md`
- Verification: content inspection
- Result: New projects copied from the template can inherit collaboration and data-architecture guidance instead of inventing it per repo.
- Resume from: use the template normally and specialize `COLLABORATION.md` or `DATA_ARCHITECTURE.md` inside project repos.

### 2026-04-15 - Clarified empty-task startup workflow

- Summary: Updated the agent router and active task dashboard so agents use the PRD/task-generation workflow when no active task exists instead of inventing tasks directly in root `TASKS.md`.
- Files touched: `AGENTS.md`, `TASKS.md`, `PROJECT_STATE.md`
- Verification: content inspection
- Result: cold-start agents are directed to generate `tasks/prd-[feature-name].md` and `tasks/tasks-[feature-name].md` before implementation work.
- Resume from: choose a feature idea and run the PRD workflow

### 2026-04-15 - Added PRD and task-generation workflow prompts

- Summary: Added local copies of the AI Dev Tasks PRD and task-list prompts, created a tracked `tasks/` directory for generated feature documents, and documented the workflow in repo docs.
- Files touched: `README.md`, `PROCESS.md`, `DECISIONS.md`, `PROJECT_STATE.md`, `prompts/ai-dev-tasks/README.md`, `prompts/ai-dev-tasks/create-prd.md`, `prompts/ai-dev-tasks/generate-tasks.md`, `tasks/README.md`
- Verification: file existence and content inspection
- Result: ready to generate PRDs into `tasks/prd-[feature-name].md` and implementation plans into `tasks/tasks-[feature-name].md`
- Resume from: choose a feature idea and run the PRD workflow

### YYYY-MM-DD - Initial state

- Summary: Template created.
- Files touched: none
- Verification: none
- Result: ready for setup
- Resume from: fill in after first work session

## Open Questions

- TODO

## Known Risks / Watchouts

- TODO
