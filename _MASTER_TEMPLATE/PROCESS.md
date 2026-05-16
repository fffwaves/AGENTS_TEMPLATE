# PROCESS.md

This file describes how to work in this repo. Keep project-specific commands and conventions here, not in `AGENTS.md`.

## Development Flow

1. Read `README.md` for setup, stack, and commands.
2. Read `PROJECT_STATE.md` for current status and last work.
3. Read `RULES.md` for project-specific rules.
4. Read `COLLABORATION.md` when other collaborators or AI harnesses are active.
5. Check `TASKS.md` for active work.
6. Pick one task or clarify scope.
7. Make the smallest scoped change that solves the task.
8. Add or update tests when behavior changes.
9. Run the relevant verification command.
10. Mark completed tasks in `TASKS.md`.
11. Update `PROJECT_STATE.md` with what changed, verification, and next steps.
12. Update `DECISIONS.md` if the work introduced or depended on a durable decision.
13. Commit when stable, unless told not to.

## Collaboration

- Use `COLLABORATION.md` as the shared workflow for multi-human or multi-agent work.
- Work on a branch for non-trivial changes.
- Do not push to `main` without explicit approval.
- Do not deploy, change production config, update webhooks, or run destructive data changes without explicit approval naming the action and scope.
- Record task ownership before editing when multiple collaborators are active.
- Use the handoff format in `COLLABORATION.md` when pausing or handing work to another collaborator.

## Persistence Rules

- `PROJECT_STATE.md` is the first place to check project continuity.
- Update `PROJECT_STATE.md` after every completed task, fix, or meaningful investigation.
- The update must include date, summary, files touched, verification run, current status, and next step.
- If work stops mid-task, update `PROJECT_STATE.md` with the partial state and exact resume point.
- `DECISIONS.md` stores durable choices, exceptions, and rationale.
- Update `DECISIONS.md` when choosing an API, library, architecture, workflow, naming convention, deployment path, or exception to normal practice.
- Do not bury durable decisions only in chat, commits, or task checklists.
- `TASKS.md` says what is active. `PROJECT_STATE.md` says what actually happened.

## Planning

- For tasks with more than roughly five steps, write a short plan before editing.
- For non-trivial work, identify requirements, constraints, architecture risks, and success criteria.
- Be explicit about what should not change.
- If minimalism is requested, avoid extra abstractions, files, dependencies, or broad rewrites.
- Update the plan when discoveries change the approach.

## Requirements

- For new projects or major features, write or request a PRD before implementation.
- Ask only essential clarifying questions before writing a PRD.
- Clarifying questions should focus on problem, core functionality, scope boundaries, and success criteria.
- PRDs should be clear enough for a junior developer to implement.
- PRDs should include goals, user stories, functional requirements, non-goals, technical constraints, success metrics, and open questions when relevant.

## PRD and Task Generation

- Use `prompts/ai-dev-tasks/create-prd.md` to generate PRDs for new projects or major features.
- Save generated PRDs as `tasks/prd-[feature-name].md`.
- Use `prompts/ai-dev-tasks/generate-tasks.md` to generate implementation tasks from a PRD.
- Save generated task lists as `tasks/tasks-[feature-name].md`.
- Keep root `TASKS.md` as the short active-work dashboard, with links or pointers to generated task files when useful.
- Do not start implementation during PRD generation.
- When generating tasks, pause after parent tasks and wait for user confirmation before adding subtasks.

## Task Files

- For large features, generate high-level parent tasks first, confirm direction, then generate subtasks.
- Task lists should include relevant files and matching test files where applicable.
- Check off subtasks as they are completed, not only at the end.
- Put tests beside the code under test when that matches project convention.

## Implementation Rules

- Prefer existing project patterns, helpers, and abstractions.
- Add new abstractions only when they reduce real complexity or match an established local pattern.
- Keep edits close to the module, ownership boundary, and behavioral surface implied by the request.
- Use structured parsers or APIs for structured data when available.
- Add comments only where they clarify non-obvious logic.
- Avoid unrelated refactors and formatting churn.

## Testing Rules

- Before writing tests, identify:
  - the core user-facing functionality
  - the highest-risk logic branches
  - the external dependencies
  - the expected success, failure, and edge-case behavior
- Write tests in that order of priority.
- Test only public behavior and observable outcomes.
- Cover every main feature with at least one happy path, one error path, and one edge case.
- Prioritize business-critical logic over simple rendering or implementation details.
- Add tests for boundaries, invalid input, empty states, and state transitions.
- Mock only external dependencies such as APIs, database calls, time, randomness, and filesystem.
- Do not over-mock internal logic.
- Keep each test focused on one behavior.
- Use clear test names that describe the scenario and expected result.
- Prefer realistic usage patterns over internal assertions.
- Avoid redundant or low-value tests.
- Add regression tests for previously broken behavior.
- Keep tests deterministic and stable.

## Verification

- Verify early and often, not only at the end.
- Break complex work into stable checkpoints and verify each checkpoint.
- End coding work with a machine-verifiable check when possible:
  - tests
  - build
  - typecheck
  - lint
  - file existence check
  - relevant command output inspection
- If a verification command cannot be run, state why.
- Do not rely only on manual reasoning when a concrete check is available.

## Anti-Loop Rules

- If the same tool call fails twice with the same error signature, stop repeating it.
- After two strikes, change approach.
- Change approach by inspecting the input differently, using another tool, simplifying the task, or asking for clarification if blocked.
- Do not retry deterministic failures a third time without changing strategy.

## Safety

- Do not exfiltrate private data.
- Do not run destructive commands without explicit approval.
- Do not push to `main`, deploy production, change webhooks, change production environment variables, or run paid/high-volume provider calls without explicit approval.
- Prefer recoverable deletion over permanent deletion.
- Ask before actions that leave the machine or affect external systems, unless already clearly requested.
- Do not commit secrets, API keys, credentials, or private tokens.
- Keep secrets out of logs, summaries, screenshots, and final responses.
- New repositories default to private.
- Public repositories require explicit approval.

## External APIs

- Any loop over an external API needs rate limiting before the first run.
- Dry-runs and tests must still respect rate limits.
- Add retry and backoff before the first production-like run, not after the first rate-limit failure.

## Documentation

- Keep repo instructions short and project-specific.
- Capture repo-specific truths: commands, conventions, test flow, folder quirks, deployment notes, and gotchas.
- If the same mistake is corrected twice, add a rule.
- Good docs read like notes to self if you had amnesia, not generic onboarding docs.
