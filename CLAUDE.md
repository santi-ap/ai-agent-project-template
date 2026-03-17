# CLAUDE.md

This file provides guidance to Claude Code when working in this repository.

> **IMPORTANT:**
> Read **`AGENTS.md`** first. It contains the shared project context and workflows.

---

## Gemini CLI Integration

To save tokens and leverage specialized capabilities, you **MUST** delegate QA and Git tasks to **Gemini CLI**.

### Mandatory Delegation
1.  **QA Gate:** After code changes, invoke Gemini to run tests.
    *   `gemini --yolo "Run verification commands and report any failures."`
2.  **Git Operations:** Once tests pass, invoke Gemini to handle staging, commits, and PRs.
    *   `gemini --yolo "Tests passed. Commit these changes and prepare a PR."`
3.  **PR Gate:** After Gemini creates the PR, verify it is merged before starting the next task. Check: `gh pr view N --json state` must be `MERGED`. If Gemini failed to create or merge the PR, Claude handles it directly via `gh pr merge + git pull origin master`.
4.  **Task Updates:** Delegate `tasks/*.md` updates to Gemini.
    *   `gemini --yolo "Mark step 'Update UI' as [-] in tasks/feat-ui.md"`

---

## Learning System

### Post-Conversation Logging
After every conversation, log mistakes, workarounds, or project patterns to `.claude/steering/learning.md`.

- Format: `err/pat/trick | title — lesson` (max ~120 chars).
- Append under `## YYYY-MM-DD` date headers.

### Slash Commands
- `/tidy-learnings` — deduplicate and trim `.claude/steering/learning.md`.
---

## Global Template Updates

Whenever `AGENTS.md`, `CLAUDE.md`, or `GEMINI.md` are updated with a new general-purpose (non-project-specific) rule or workflow — whether you discovered it during work or the user added it directly — you **must** delegate the same change to the template repo:
- **Delegate to Gemini:** Ask Gemini to apply the change to `santi-ap/ai-agent-project-template` via a new branch.
- Example: `gemini --yolo "Update the global template repo with this new rule: [RULE DESCRIPTION]"`
