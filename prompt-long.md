# Long Reusable Prompt Template

Use this when you need Claude to understand architecture, dependencies, and decisions
made in prior sessions. Fill in the bracketed fields.

---

```
## Project Overview
Name: [project name]
Description: [one sentence — what the project does]
Stack: [languages, frameworks, databases, key libraries]
Repo: [repo URL or local path]
Branch: [current branch]
Entry point: [e.g. src/index.ts, main.py]

## Architecture
[2-4 sentences or a bullet list describing how the app is structured.
Example:
- Express server in src/server.ts handles routes
- Services in src/services/ contain business logic
- Prisma ORM with schema at prisma/schema.prisma
- React frontend in client/src/]

## What's Coded So Far
| Area           | Status      | Key Files                     |
|----------------|-------------|-------------------------------|
| [e.g. Auth]    | [done/wip]  | [src/auth/login.ts]           |
| [e.g. DB]      | [done/wip]  | [prisma/schema.prisma]        |
| [e.g. API]     | [done/wip]  | [src/routes/users.ts]         |
| [e.g. UI]      | [not started]| —                            |

## Where I Left Off
File: [filename:line]
Task: [what you were in the middle of]
Blocker: [specific error, missing dependency, design question, or "none"]
Last commit: [commit hash or message]

## What's Needed to Make It Function
### Must Have (blocks running the app)
- [ ] [task — e.g. "Add DATABASE_URL to .env and run migrations"]
- [ ] [task]
- [ ] [task]

### Should Have (core functionality gaps)
- [ ] [task]
- [ ] [task]

### Nice to Have (polish, optimization)
- [ ] [task]
- [ ] [task]

## Decisions & Constraints
- [e.g. "Using JWT, not sessions, for auth"]
- [e.g. "Postgres required — no SQLite fallback"]
- [e.g. "Must support Node 18+"]

## Rules for This Session
- Read files before editing. Never guess at contents.
- Minimal changes only — no drive-by refactors.
- Don't create new files unless strictly necessary.
- Don't add comments, types, or docstrings to unchanged code.
- Commit after completing each task.
- If blocked, stop and ask instead of guessing.
```

---

### Usage

1. Copy the block above into your first message each session.
2. Fill in every `[ ]` placeholder. Delete rows/sections that don't apply.
3. After the session, update **What's Coded So Far**, **Where I Left Off**,
   and move completed items out of **What's Needed**.
4. Save the updated prompt locally so it's ready for next time.
