---
name: load-context
description: Loads a previously saved work context into the current conversation. Use when the user wants to resume work from a prior session or pick up where they left off.
---

# load-context

Load a previously saved work context into the current conversation.

## Usage
```
/load-context {keyword}
/load-context
```

## Procedure

1. **If a keyword is provided** — search `~/.claude/context/` for `.md` files whose name contains the keyword and Read the match
2. **If no keyword is provided or no match is found** — read `~/.claude/context/index.md`, show the list, and ask the user to select an entry
