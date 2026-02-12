# Prompt: Merge Two App Versions into One

Use this prompt when you have two separate versions of the same app and want
Claude Code to combine their features into a single unified version.

Fill in the bracketed fields before pasting.

---

## Ready-to-Paste Prompt

```
## Goal
I have two versions of my Chronos app. I need you to merge them into one
complete version that includes all features from both.

## Version A — [short label, e.g. "Timer + Alerts"]
Location: [path or branch, e.g. ~/chronos-v1 OR branch: main]
What it has:
- [feature, e.g. "Countdown timer with start/stop/reset"]
- [feature, e.g. "Push notification alerts"]
- [feature, e.g. "Settings page for alert preferences"]
Key files:
- [e.g. src/components/Timer.tsx]
- [e.g. src/services/alerts.ts]
- [e.g. src/pages/Settings.tsx]

## Version B — [short label, e.g. "Scheduling + History"]
Location: [path or branch, e.g. ~/chronos-v2 OR branch: feature/scheduling]
What it has:
- [feature, e.g. "Event scheduling with calendar view"]
- [feature, e.g. "Session history log"]
- [feature, e.g. "Export history to CSV"]
Key files:
- [e.g. src/components/Calendar.tsx]
- [e.g. src/services/history.ts]
- [e.g. src/utils/export.ts]

## Merge Target
Location: [where the merged version should live, e.g. ~/chronos-merged OR new branch: merged]
Base: [which version to use as the base — A or B, and why]

## Conflicts & Preferences
- If both versions define [e.g. the main layout], keep [A's / B's / describe preference].
- If both versions have [e.g. a settings page], combine them into one page with sections for each.
- Shared dependencies: [note any version mismatches you're aware of, or "unknown — check both package.json files"]
- [Any other merge rules, e.g. "B's routing structure is better — use that as the base for navigation"]

## Steps I Want You to Follow
1. Read both versions fully before making any changes.
2. List every feature from each version side by side.
3. Identify overlapping files, conflicting logic, and dependency differences.
4. Present a merge plan and wait for my approval before writing code.
5. Merge incrementally — one feature area at a time, committing after each.
6. After merging, list anything that still needs manual testing or wiring up.

## Rules
- Do NOT delete features from either version.
- Do NOT refactor or "improve" code during the merge.
- If two implementations conflict, stop and ask which one I want.
- Commit after each merged feature area with a clear message.
```

---

## How to Fill This In

**If your two versions are in separate folders:**
```
Version A Location: ~/projects/chronos-timer
Version B Location: ~/projects/chronos-scheduler
Merge Target: ~/projects/chronos-complete
```

**If your two versions are on separate git branches:**
```
Version A Location: branch: main
Version B Location: branch: feature/scheduling
Merge Target: branch: merged-complete
```

**If you're not sure what's in each version**, shorten the prompt:

```
## Goal
I have two versions of my Chronos app. Before merging, read both and tell me:
1. What features exist in each version
2. What files overlap or conflict
3. A proposed merge plan

Version A: [location]
Version B: [location]

Do NOT make any changes yet. Just analyze and report back.
```

This "analyze first" version saves tokens if Claude discovers the versions are
more different than you expected — you can adjust the plan before any code is written.

---

## Tips

- **Use the "analyze first" version** if you haven't looked at both codebases recently.
  It's cheaper to read a summary than to undo a bad merge.
- **Pick a base version.** Merging works best when one version is the foundation
  and the other's features are added into it. Whichever version has more
  infrastructure (routing, auth, DB setup) is usually the better base.
- **Merge one area at a time.** Don't ask Claude to merge everything in one shot.
  Go feature by feature so you can test as you go.
- **After the merge**, paste the short or long session template with updated
  status so future sessions know the merge is done and what's left.
