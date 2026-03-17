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
3.  **Task Updates:** Delegate `tasks/*.md` updates to Gemini.
    *   `gemini --yolo "Mark step 'Update UI' as [-] in tasks/feat-ui.md"`

---

## Learning System

### Post-Conversation Logging
After every conversation, log mistakes, workarounds, or project patterns to `.claude/steering/learning.md`.

- Format: `err/pat/trick | title — lesson` (max ~120 chars).
- Append under `## YYYY-MM-DD` date headers.

### Slash Commands
- `/tidy-learnings` — deduplicate and trim `.claude/steering/learning.md`.
- `/compress-memory` — compress old entries into `.claude/steering/long_term_memory.md`.
