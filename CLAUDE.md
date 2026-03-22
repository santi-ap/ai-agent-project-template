# CLAUDE.md

This file provides guidance to Claude Code when working in this repository.

> **IMPORTANT:**
> Read **`AGENTS.md`** first. It contains the shared project context and workflows.

---

## Gemini Consultation (Rubber Duck)

Use Gemini as a thinking partner to pressure-test plans or catch blind spots — **not** for QA or Git.

### When to consult Gemini
- Before starting a non-trivial task: validate your implementation approach
- When stuck on a design decision: ask for alternatives
- When your plan feels risky: ask Gemini to poke holes in it

### How to consult
1. Call Gemini with a focused prompt:
   `gemini --yolo "Here is my plan for [task]. Identify any flaws or improvements."`
2. **Sleep after the call** to avoid hitting Gemini quota limits between AI agents:
   - Simple / short prompt → sleep 10s
   - Medium complexity → sleep 20s
   - High complexity / long context → sleep 40s
3. Incorporate useful feedback, then proceed independently.

### What Claude handles directly (no Gemini delegation)
- Running tests and linting
- Git operations: branching, staging, committing, PRs via `gh`
- Task file updates: `tasks/*.md` checkboxes
- Template sync: apply changes to `santi-ap/ai-agent-project-template` directly

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

If you discover a new, non-project-specific rule or workflow that should apply to **all** projects, apply the change directly:
1. Create a new branch in `ai-agent-project-template`.
2. Apply the change to the corresponding file(s), push, open a PR, and merge it (`gh pr merge --merge`).
3. Do NOT delete the branch after the merge.
