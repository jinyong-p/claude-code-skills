# Context Skills

Persist and restore work context across Claude Code conversations.

## When to use

- A long-running task spans multiple conversations
- The conversation context grows too long and you need to start fresh
- You use git worktrees and switch between different features frequently
- You want to save progress before ending the day and resume tomorrow

## What it does

When working on a long-running task across multiple Claude Code sessions, context is lost between conversations. These two skills solve that:

- **`/save-context`** — Captures the current conversation's key information (branch, architecture, task progress) and writes it to a structured markdown file in `~/.claude/context/`.
- **`/load-context`** — Reads a saved context file back into a new conversation so you can pick up where you left off.

An `index.md` file in the context directory acts as a table of contents for all saved contexts.

## File structure

```
~/.claude/
├── context/                  # Saved context files (created on first use)
│   ├── index.md              # Table of contents
│   ├── my-feature.md         # Example saved context
│   └── another-project.md
└── skills/
    ├── save-context/
    │   └── SKILL.md          # Skill definition
    └── load-context/
        └── SKILL.md          # Skill definition
```

## Installation

```bash
# Clone the repo
git clone <repo-url> ~/claude-code-skills

# Copy skills
cp -r ~/claude-code-skills/context/save-context ~/.claude/skills/save-context
cp -r ~/claude-code-skills/context/load-context ~/.claude/skills/load-context

# Create the context directory
mkdir -p ~/.claude/context
```

## Usage

```
# Save context with a keyword
/save-context my-feature

# Save context interactively (shows index, lets you pick or create)
/save-context

# Load context by keyword
/load-context my-feature

# Load context interactively
/load-context
```

## Context file format

Each saved context file contains:

| Section | Description |
|---------|-------------|
| Overview | 1-2 line summary of the task |
| Branch info | Current git branch |
| Architecture | Data flow, module structure, key models, infra |
| Completed tasks | What's done (with issue numbers if available) |
| In-progress tasks | What's actively being worked on |
| TODO | What's left to do |
