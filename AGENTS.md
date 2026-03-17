# AGENTS.md

This file is the **central knowledge base** for all AI agents working on this project. It defines the shared context, architectural patterns, and mandatory workflows.

---

## Language & Coding Standards

- **Language:** [PRIMARY LANGUAGE, e.g., TypeScript]
- **Typing:** Use strong typing; avoid `any`. Use explicit interfaces for data models.
- **Conventions:** Follow [PRIMARY STYLE GUIDE, e.g., Airbnb, Google].

---

## Mandatory Workflows

### 1. Task File Requirement ⚠️
Every feature, bug fix, refactor, or similar work **MUST** begin by creating a task file in `tasks/` before any code is written.

- **File name:** `tasks/<type>-<description>.md` (e.g., `tasks/feat-auth-login.md`, `tasks/bug-fix-api-crash.md`)
- **Format:** Use nested checkboxes and emoji-prefixed titles (e.g., `# ✨ Feature:`, `# 🐛 Bug Fix:`).
- **Status Mapping:**
  - `[ ]` = Todo
  - `[-]` = In Progress (started but not finished)
  - `[x]` = Done (fully complete and verified)

### 2. Mandatory Task Status Updates
**All agents MUST update task file checkboxes in real-time.**
1. **Before starting a step** → change `[ ]` to `[-]` immediately.
2. **After completing a step** → change `[-]` to `[x]` immediately.
3. **Never batch updates** — update the file as each step begins/ends.

### 3. Git & Branching Workflow 🌿
- **No Direct Master Commits:** All work must be performed on a dedicated branch. NEVER work directly on `master`.
- **Branch Creation:** When starting a new task, create a new branch from `master`.
- **Pre-flight Pull:** Always `git pull origin master` before starting work on a new branch to ensure it is up-to-date.
- **PR Process:** Once a task is complete and all tests pass, create a Pull Request (PR) to merge into `master`.

### 4. Verification & QA Gate 🧪
- **Unit Tests:** All new features must include unit tests. All local unit tests must pass before pushing to the repository.
- **QA Agent (Gemini):** Responsible for running unit tests and reporting results.
- **Execution:** Claude may trigger a test run by telling Gemini to do it with the `--yolo` flag.
- **Failure Handling:**
  - If tests fail and the fix is **trivial**, Gemini handles the fix.
  - If the failure is **non-trivial**, Claude must fix the reported issue and ask Gemini to re-verify.

---

## Agent Roles & Responsibilities

- **Claude Code:** Primary code architect and implementer. Focuses on logic and feature implementation.
- **Gemini CLI:** Primary **QA, Git, and Task Operator**.
    - **QA:** Runs tests and verification commands after code changes.
    - **Git:** Handles branching, staging, commits, and PRs **only after verification passes**.
    - **Task Updates:** Updates `tasks/*.md` checkboxes as work progresses.

---

## Commands & Architecture

### Key Commands
```bash
# [ADD PROJECT SPECIFIC COMMANDS HERE]
# e.g., npm run test, go test ./..., ruff check .
```

### Architecture Overview
---

## Global Template Updates 🌍

This project uses a base template from `santi-ap/ai-agent-project-template`.

**Mandatory Rule:** If a new general-purpose (non-project-specific) instruction, rule, or workflow improvement is discovered during this project:
1.  **GEMINI:** Create a new branch in the `ai-agent-project-template` repository.
2.  **GEMINI:** Apply the improvement to the template and push the branch.
3.  **GEMINI:** Create a Pull Request (PR) to merge the branch into `master` to ensure the template stays current.
4.  **GEMINI:** Merge the PR to `master` immediately (using `gh pr merge --merge`).
5.  **GEMINI:** Do NOT delete the branch after the merge.
6.  This ensures that every future project benefits from learnings in this one.
