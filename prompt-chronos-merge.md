# Chronos App Merge Prompt — Ready to Paste

Copy the prompt below directly into your Claude Code web terminal.
No placeholders to fill in — it's ready to go.

---

## Prompt 1: Analyze First (Recommended — Start Here)

Paste this first to let Claude read all three projects before touching anything.
This saves tokens if the projects are more different than expected.

```
## Goal
I have three versions of my Chronos app in separate folders. Before making
any changes, read all three and give me:
1. What features and files exist in each version
2. What files overlap or conflict across versions
3. A proposed merge plan

## Locations
Base project:     C:\Users\jlittleton\Desktop\Full ProjectforGoogle\Full Project\project #1.0
UI source 1:      C:\Users\jlittleton\Desktop\Full ProjectforGoogle\Full Project\project #1.1
UI source 2:      C:\Users\jlittleton\Desktop\Full ProjectforGoogle\Full Project\project #2.0

## What I Know
- Project #1.0 is the BASE. It has the correct timeline & subevent structure.
  This structure MUST be preserved exactly.
- Project #1.1 has UI design improvements and new features built on top of #1.0.
- Project #2.0 has additional UI design features and new functionality.
- I want to merge the UI and new features from #1.1 and #2.0 INTO #1.0's
  foundation without breaking its timeline & subevent logic.

Do NOT make any changes yet. Just analyze all three projects and report back
with a feature comparison table and a merge plan.
```

After Claude reports back, review the plan. Then paste Prompt 2.

---

## Prompt 2: Execute the Merge

Paste this after you've reviewed and approved Claude's analysis from Prompt 1.

```
## Goal
Merge the UI design features and new functionality from project #1.1 and
project #2.0 into project #1.0 as the base, producing one complete version.

## Source Projects
BASE (structure & logic):  C:\Users\jlittleton\Desktop\Full ProjectforGoogle\Full Project\project #1.0
UI + features source A:    C:\Users\jlittleton\Desktop\Full ProjectforGoogle\Full Project\project #1.1
UI + features source B:    C:\Users\jlittleton\Desktop\Full ProjectforGoogle\Full Project\project #2.0

## Merge Rules — READ CAREFULLY
1. Project #1.0 is the foundation. Its timeline structure and subevent logic
   are the source of truth. NEVER overwrite or restructure them.
2. Bring in UI design improvements from #1.1 (styles, layout, components).
3. Bring in UI design improvements and new features from #2.0.
4. If #1.1 and #2.0 both changed the same file differently, STOP and ask me
   which version I want, or whether to combine both.
5. If any UI change from #1.1 or #2.0 would require modifying the timeline
   or subevent data model from #1.0, STOP and ask me before proceeding.
6. Keep all new features from #1.1 and #2.0 — do not drop anything.

## Where to Put the Merged Version
Create a new folder:
C:\Users\jlittleton\Desktop\Full ProjectforGoogle\Full Project\chronos-merged

Copy project #1.0 into this folder first as the base, then layer in changes
from #1.1 and #2.0.

## Steps
1. Copy project #1.0 to the chronos-merged folder.
2. Identify every file in #1.1 that differs from #1.0. For each:
   - If it's a UI/style change, apply it to the merged copy.
   - If it's a new file (new feature), add it to the merged copy.
   - If it touches timeline/subevent logic, flag it and ask me.
3. Do the same for project #2.0.
4. Resolve any conflicts between #1.1 and #2.0 changes — ask me if unsure.
5. After all merges, list:
   - What was added from #1.1
   - What was added from #2.0
   - Any files that still need manual review or testing
6. Commit after each major feature area is merged.

## Rules
- Do NOT refactor, rename, or "improve" any code during the merge.
- Do NOT delete features from any version.
- Do NOT modify #1.0's timeline or subevent structure unless I approve it.
- If something conflicts, STOP and ask. Do not guess.
- Be concise in responses to save tokens.
```

---

## Quick Reference

| Project   | Role in Merge                                    |
|-----------|--------------------------------------------------|
| #1.0      | **BASE** — timeline & subevent structure (sacred)|
| #1.1      | UI design improvements + new features            |
| #2.0      | Additional UI design + new features              |
| merged    | Final output in `chronos-merged` folder          |

## Workflow

```
Session 1:  Paste Prompt 1 → Claude analyzes all 3 projects → You review
Session 2:  Paste Prompt 2 → Claude merges incrementally → You test each step
Session 3+: Use prompt-short.md with updated status to continue any leftover work
```
