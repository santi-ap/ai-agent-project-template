# Project AI Template

This folder contains a set of instruction files to bootstrap AI agent workflows (Claude Code & Gemini CLI) in any new project.

## Quick Start

1.  **Copy** all files/folders from this template into your new project root.
2.  **Edit `AGENTS.md`**:
    *   Set the `Language` and `Coding Standards`.
    *   Add your project's `Key Commands` (test, lint, etc.).
    *   Fill in the `Architecture Overview`.
3.  **Ensure `tasks/` folder exists**: This is where you will define all work items before starting.
4.  **Inform the AI**:
    *   Claude: "Please read AGENTS.md and CLAUDE.md to understand our workflow."
    *   Gemini: "Please read AGENTS.md and GEMINI.md to understand your role."

## Key Workflow: Task First
Always create a `.md` file in `tasks/` before writing any code. Update checkboxes from `[ ]` to `[-]` when starting and `[x]` when finishing.
