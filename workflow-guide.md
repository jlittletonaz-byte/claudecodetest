# Token-Efficient Workflow for Claude Code Web Sessions

## The Problem

Every new Claude Code web session starts with zero context. If you explain your
project from scratch each time, you burn tokens before any real work happens.

## The Solution: Session Bookmarks

Treat each session like a save point. At the end of every session, update a
prompt template with your current state. At the start of the next session, paste
it in. Claude picks up exactly where you left off.

---

## Workflow

### 1. Before Your First Session

Pick a template:
- **`prompt-short.md`** — fast, low-token overhead (~100 tokens). Good for
  simple projects or when you know exactly what to ask.
- **`prompt-long.md`** — detailed, higher context fidelity (~300 tokens). Good
  for multi-file projects, onboarding a new session into complex architecture.

Fill it in and save it locally (e.g. `my-project-session.md`).

### 2. Starting a Session

1. Open Claude Code web terminal.
2. Paste your filled-in prompt as the first message.
3. Follow up with a single, specific task:
   > "Implement the createUser function in src/services/users.ts"

**Don't** dump a list of 10 tasks. One task per exchange keeps responses focused
and avoids wasted tokens on work you didn't need yet.

### 3. During the Session

- **One task at a time.** Finish it, confirm it works, then move on.
- **Be specific.** "Fix the type error on line 42 of auth.ts" beats "fix the
  errors."
- **Don't re-explain context.** The prompt you pasted already covers it. Just
  reference file names and line numbers.
- **If Claude drifts**, say: "Stop. Only do what I asked." This is cheaper than
  letting it generate a long wrong answer.

### 4. Ending a Session

Before you close:

1. Ask Claude: "Summarize what was done this session in bullet points."
2. Copy that summary.
3. Open your saved prompt file.
4. Update these sections:
   - **Done / What's Coded So Far** — add completed work
   - **Left Off At / Where I Left Off** — file, line, task, blocker
   - **Remaining / What's Needed** — remove completed items, add new ones
5. Save the file. It's ready for next time.

---

## Token-Saving Tips

| Tip | Why |
|-----|-----|
| Use the short template for simple tasks | Fewer input tokens per session |
| Don't repeat yourself | If it's in the prompt, don't say it again |
| Ask for one thing at a time | Prevents long multi-part responses |
| Say "be concise" if answers are too long | Claude will shorten output |
| Use file paths and line numbers | Avoids Claude searching the whole repo |
| Don't ask Claude to explain code you already understand | Saves output tokens |
| End sessions early if you're stuck | Restarting with a clear prompt is cheaper than debugging in circles |

---

## Example: Session Handoff

**End of session 1 — you ask:**
> Summarize what was done.

**Claude responds:**
> - Created Express server in src/server.ts with health check route
> - Added Prisma schema with User model
> - Ran initial migration
> - Started but did not finish: POST /users route in src/routes/users.ts (line 14, missing password hashing)

**You update your prompt file and save it. Next session, you paste it and say:**
> Finish the POST /users route. Hash the password with bcrypt before saving.

No re-explaining. No wasted tokens. Claude has everything it needs from the
prompt.

---

## File Reference

| File | Purpose |
|------|---------|
| `prompt-short.md` | Minimal session prompt (~100 tokens) |
| `prompt-long.md` | Detailed session prompt (~300 tokens) |
| `workflow-guide.md` | This file — how to use the templates |
