# AGENTS_TEMPLATE

Reusable Codex project template for agent-friendly repositories.

This repo contains two things:

- `AGENTS.md` - global Codex instructions copied from `~/.codex/AGENTS.md`
- `_MASTER_TEMPLATE/` - files to copy into the root of a new project

## What This Template Does

The template gives each project a predictable structure for Codex and other AI coding agents:

- `AGENTS.md` stays tiny and acts as the instruction router.
- `README.md` explains what the project is, which stack it uses, and which commands to run.
- `RULES.md` stores project-specific rules and overrides.
- `PROCESS.md` stores the development workflow, testing rules, verification rules, safety rules, and persistence rules.
- `PROJECT_STATE.md` stores the current status, last work, next step, and resume point.
- `DECISIONS.md` stores durable decisions, exceptions, and rationale so future agents do not regress prior choices.
- `TASKS.md` stores active work only.
- `BACKLOG.md` stores future work and tiered priorities.

## How To Use

Copy the contents of `_MASTER_TEMPLATE/` into the root of any new project:

```sh
cp -R _MASTER_TEMPLATE/. /path/to/new-project/
```

Then edit these files for the project:

1. Update `README.md` with the real stack, commands, project structure, and environment variables.
2. Update `RULES.md` with project-specific conventions and exceptions.
3. Update `PROJECT_STATE.md` with the current status and first next step.
4. Update `TASKS.md` with active work.
5. Update `BACKLOG.md` with future work.

## Recommended Project Root

```txt
AGENTS.md
README.md
RULES.md
PROCESS.md
PROJECT_STATE.md
DECISIONS.md
TASKS.md
BACKLOG.md
```

## Persistence Rule

`PROJECT_STATE.md` is the continuity file. After every completed task, fix, meaningful investigation, or interrupted session, update it with:

- date
- summary
- files touched
- verification run
- current status
- next step or resume point

`DECISIONS.md` is for durable project choices and exceptions, such as API preferences, library choices, architecture constraints, deployment paths, or known deviations from normal practice.

## Global Codex Instructions

The root `AGENTS.md` in this repo is a backup of `~/.codex/AGENTS.md`. Keep it short. Global instructions should only contain universal safety and loading rules. Project workflow belongs in the project template files.