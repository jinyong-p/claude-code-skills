---
name: save-context
description: Saves the current conversation's work context (branch, architecture, task progress) to ~/.claude/context/. Use when the user wants to persist session state before ending a conversation.
---

# save-context

Save the current conversation's work context to `~/.claude/context/`.

## Usage
```
/save-context {keyword}
/save-context
```

## Procedure

1. **Resolve keyword**
   - If a keyword is provided, search `~/.claude/context/` for a matching file
   - If no keyword is provided, read `~/.claude/context/index.md`, show the list, and ask the user to select an entry or create a new one

2. **Save context file**
   - File path: `~/.claude/context/{keyword}.md`
   - If the file already exists, Read it first and merge/update; otherwise create a new file
   - Contents:
     - Overview (1-2 lines)
     - Branch info
     - Architecture (data flow, module structure, key models, infra)
     - Completed tasks
     - In-progress tasks
     - TODO

3. **Update index.md**
   - Add an entry to `~/.claude/context/index.md` if one doesn't already exist
   - Format: `| {keyword} | {description} | [{filename}](./{filename}) |`

## Writing principles
- Minimize tokens: be concise, remove unnecessary explanation
- Use module-level code paths (e.g. `order/`, `payment/`)
- Track completed / in-progress / TODO items by issue number when available
