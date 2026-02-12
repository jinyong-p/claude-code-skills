# claude-code-skills

Custom skills (slash commands) for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI.

## Available Skills

| Skill | Description |
|-------|-------------|
| [context](./context/) | Save and restore work context across conversations (`/save-context`, `/load-context`) |

## Installation

Each skill directory contains its own README with installation instructions. The general pattern is:

```bash
cp -r /path/to/claude-code-skills/<skill-dir>/<skill-name> ~/.claude/skills/<skill-name>
```

See individual skill READMEs for details.
