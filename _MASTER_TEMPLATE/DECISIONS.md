# DECISIONS.md

Durable project decisions, exceptions, and rationale. Update when a choice should affect future work.

## Decisions

### 2026-05-16 - Add collaboration and data architecture templates

- Decision: Add generic `COLLABORATION.md` and `DATA_ARCHITECTURE.md` docs to the master template and route agents to them from `AGENTS.md` and `PROCESS.md`.
- Rationale: Projects may involve multiple humans and AI harnesses, shared-state actions, production systems, paid providers, or durable data flows. The template should make those rules explicit before they become project-specific problems.
- Applies to: New projects copied from this template, collaboration workflows, approval gates, storage guidance, caching guidance, and generated data docs.
- Revisit when: The template adopts a different collaboration or architecture planning system.

### 2026-04-15 - Store AI development workflow prompts locally

- Decision: Store reusable AI workflow prompts under `prompts/ai-dev-tasks/` and generated feature PRDs/task lists under `tasks/`.
- Rationale: The prompts are reusable process assets, while generated PRDs and task lists are feature-specific working documents. Keeping root `TASKS.md` short preserves its role as the active-work dashboard.
- Applies to: PRD creation, task generation, and feature planning workflows.
- Revisit when: The repo adopts a different planning system or needs generated task files stored outside source control.

## Active Exceptions

- TODO: Example: Use Brave API instead of Exa for specific sources because Exa cannot access them reliably.
