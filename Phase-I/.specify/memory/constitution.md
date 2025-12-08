<!--
Sync Impact Report:
Version change: template -> 1.0.0
List of modified principles: None (initial setup)
Added sections: Versioning and date information
Removed sections: None
Templates requiring updates:
  - .specify/templates/plan-template.md ⚠ pending
  - .specify/templates/spec-template.md ⚠ pending
  - .specify/templates/tasks-template.md ⚠ pending
  - .claude/commands/sp.adr.md ⚠ pending
  - .claude/commands/sp.analyze.md ⚠ pending
  - .claude/commands/sp.checklist.md ⚠ pending
  - .claude/commands/sp.clarify.md ⚠ pending
  - .claude/commands/sp.constitution.md ⚠ pending
  - .claude/commands/sp.git.commit_pr.md ⚠ pending
  - .claude/commands/sp.implement.md ⚠ pending
  - .claude/commands/sp.phr.md ⚠ pending
  - .claude/commands/sp.plan.md ⚠ pending
  - .claude/commands/sp.specify.md ⚠ pending
  - .claude/commands/sp.tasks.md ⚠ pending
  - .gemini/commands/sp.adr.toml ⚠ pending
  - .gemini/commands/sp.analyze.toml ⚠ pending
  - .gemini/commands/sp.checklist.toml ⚠ pending
  - .gemini/commands/sp.clarify.toml ⚠ pending
  - .gemini/commands/sp.constitution.toml ⚠ pending
  - .gemini/commands/sp.git.commit_pr.toml ⚠ pending
  - .gemini/commands/sp.implement.toml ⚠ pending
  - .gemini/commands/sp.phr.toml ⚠ pending
  - .gemini/commands/sp.plan.toml ⚠ pending
  - .gemini/commands/sp.specify.toml ⚠ pending
  - .gemini/commands/sp.tasks.toml ⚠ pending
  - README.md ⚠ pending
  - CLAUDE.md ⚠ pending
Follow-up TODOs: None
-->
# Constitution — Phase I: In-Memory Python Todo CLI App

## 1. Purpose
This constitution defines the rules for Phase I of the "Evolution of Todo" project.
All implementation must be spec-driven using Claude CLI + SpecKit Plus.
The developer will not write code manually; Claude must generate all source code from specs.

## 2. Project Scope
Create an in-memory Python CLI Todo application with the following features:
- Add Task
- View Tasks
- Update Task
- Delete Task
- Mark Complete / Incomplete

All tasks must exist only in memory (no database).
Application must run in a terminal using Python 3.13+.

## 3. Architecture Rules
- Source code lives under `src/todo/`.
- Keep modules small and single-responsibility.
- Use:
  - `models.py` → task model + dataclasses or simple classes
  - `storage.py` → in-memory storage abstraction
  - `services.py` → business logic
  - `cli.py` → command-line UI
  - `main.py` → entrypoint

## 4. Data Model
A Task must include:
- `id: int`
- `title: str`
- `description: str`
- `completed: bool` (default False)
- `created_at: str`
- `updated_at: str`

Timestamps must be ISO formatted using Python datetime.

## 5. Coding Standards
- Python 3.13
- Type hints required
- Docstrings for all classes/functions
- No external libraries
- Clean, readable, single-purpose functions
- No global mutable state outside the storage component

## 6. CLI Requirements
- User can add, list, update, delete, complete, incomplete tasks
- Simple commands: `add`, `list`, `update <id>`, `delete <id>`, `complete <id>`, `incomplete <id>`, `exit`, `help`
- CLI must print clear messages and handle invalid input gracefully

## 7. Tests
- Tests live in `tests/`
- Use pytest style
- Each feature must have at least one test
- Storage must reset per test (isolated state)

## 8. Spec-Driven Rules
Claude must follow this workflow:
1. `/sp.specify` → feature spec
2. `/sp.plan`
3. `/sp.task`
4. `/sp.implement`

Claude must:
- Not hallucinate files outside this structure
- Follow this constitution for every generation
- Update code only through the spec-driven workflow
- Generate tests first, then implementation

## 9. Completion Criteria
Phase I is complete when:
- All 5 features are implemented
- All tests pass
- CLI works end-to-end
- Repo contains: Constitution.md, specs/, src/, tests/, README.md, CLAUDE.md

**Version**: 1.0.0 | **Ratified**: 2025-12-07 | **Last Amended**: 2025-12-07