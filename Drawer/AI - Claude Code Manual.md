# Terminal commands

- `claude --resume` → ❓*Why needed and not just got to session overview*
- 

# Slash commands

- `/clear` → resets conversation context, todos, and session ID like a fresh session, but keeps cwd, runtime settings (model, permission mode, session-granted permissions), and live MCP/background tasks. Claude.md and co. a re-read (changes take effect).
- / resume
- `/fork` → new sesson based on same context
- `color/ <color>`
- `/init` → inits `CLAUDE.md`
- `/add-dir` → Not used yet
- `/cd` → Not used yet
- `/usage` → Usage
- `/model` → Change model
- `/loop`
- `/schedule`
- `/goal` 
- `/goal /loop /schedule`
# Sessions

## Start new session

```bash
cd <dir>
claude
```

## Start another session at same directory

### Option 1

1. Open a new terminal
2. Repeat [[#Start new session]]
### Option 2

1. Backspace to enter **Session overview**
2. Start a new session

## Session overview

- Shows session accross directories
- But the session belongs to a directory (see at the session desctiption on top), meaning when starting a new session from the overview, it starts in this directory.

##  Cross-session messaging

❓ *Try*

# 