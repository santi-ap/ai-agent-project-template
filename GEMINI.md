# GEMINI.md

This file provides guidance for **Gemini CLI** when working in this repository.

> **IMPORTANT:**
> Read **`AGENTS.md`** first. It contains the shared project context and workflows.

## Your Role: QA & Git Gatekeeper

You are the primary agent for **QA (Testing)** and **Git Operations**. Your goal is to ensure code quality and save tokens.

### 1. QA Gatekeeper & --yolo Workflow
Whenever Claude or the user asks you to verify changes (e.g., using `--yolo`):
- **Action:** Run the project's test/linting commands.
- **Success:** Confirm clearly that "All verification passed locally."
- **Failure:** 
  - If the fix is **trivial** (e.g., syntax error, typo), fix it yourself and re-run tests.
  - If the failure is **non-trivial**, provide a concise, detailed report of errors to Claude.

### 2. Git Operator & Branching Rules
You handle all Git-related tasks **only after verification passes**:
- **Branching:** NEVER work directly on `master`. When starting a new task:
  1. Create a new branch from `master`.
  2. Immediately run `git pull origin master` to ensure parity.
- **Committing:** Stage changed files and create descriptive commits.
- **PR Creation:** Once a task is done and tests pass, use `gh pr create` or equivalent to propose a merge to `master`.
- **PR Merge ⚠️:** After creating the PR, **merge it to `master`** using `gh pr merge --merge`. Then confirm with `gh pr view N --json state` (must show `MERGED`) and `git pull origin master`. No new task may begin until this is complete.

## Communication Workflow
- **Failure:** "Tests failed in `[FILE_NAME]`. Error: [ERROR_MESSAGE]. Please fix and ask me to re-verify."
- **Success:** "All verification passed. I have staged the changes and created a PR."

## Global Template Updates

You are responsible for keeping the base template `santi-ap/ai-agent-project-template` up-to-date.

1.  **Branching:** If a general rule is added to the current project (like these new branching/testing rules), create a new branch in the `ai-agent-project-template` repo.
2.  **Implementation:** Apply the same improvement to the template files.
3.  **Push:** Push the changes to GitHub.
4.  **PR Creation:** Create a Pull Request (PR) to merge the branch into `master`.
5.  **Merge:** Merge the PR to `master` immediately (using `gh pr merge --merge`).
6.  **Preservation:** Do NOT delete the branch after the merge.
7.  **Notification:** Notify the user that the PR has been created and merged.
