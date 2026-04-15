# DECISIONS.md

Durable project decisions, exceptions, and rationale. Update when a choice should affect future work.

## Decisions

### 2026-04-15 - Store AI development workflow prompts locally

- Decision: Store reusable AI workflow prompts under `prompts/ai-dev-tasks/` and generated feature PRDs/task lists under `tasks/`.
- Rationale: The prompts are reusable process assets, while generated PRDs and task lists are feature-specific working documents. Keeping root `TASKS.md` short preserves its role as the active-work dashboard.
- Applies to: PRD creation, task generation, and feature planning workflows.
- Revisit when: The repo adopts a different planning system or needs generated task files stored outside source control.

## Active Exceptions

- TODO: Example: Use Brave API instead of Exa for specific sources because Exa cannot access them reliably.
