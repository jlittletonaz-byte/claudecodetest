# Short Reusable Prompt Template

Paste this at the start of every new Claude Code web session. Fill in the bracketed fields.

---

```
## Context
Project: [project name]
Stack: [e.g. Node/Express/Postgres]
Repo: [repo URL or local path]
Branch: [current branch]

## Done
- [feature/file completed]
- [feature/file completed]

## Left Off At
File: [filename:line]
Task: [what you were doing]
Blocker: [issue if any, or "none"]

## Remaining
- [ ] [next task]
- [ ] [next task]
- [ ] [next task]

## Rules
- Read before editing. No guessing.
- Minimal changes only. No refactors unless asked.
- No new files unless required.
- Commit after each task with a clear message.
```

---

### Usage

1. Copy the block above into your first message.
2. Fill in each `[ ]` placeholder.
3. As you finish tasks, move items from **Remaining** to **Done** and update **Left Off At**.
4. Paste the updated version when you start your next session.
