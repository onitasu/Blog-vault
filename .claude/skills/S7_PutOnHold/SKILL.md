---
name: S7_PutOnHold
description: Mark a theme/draft/context as on-hold and record missing pieces so S3 can recommend resuming later.
allowed-tools:
  - Read
  - Edit
  - Write
  - Grep
  - Glob
---

# S7_PutOnHold

## Inputs
- draft_path

## Steps
1) Find linked theme_id and context file from the draft (or ask user).
2) Update theme note:
   - status: on_hold
   - Fill "On-hold gaps" with specific missing items.
3) Update context file status: on_hold and record missing items.
4) Update draft with a short on-hold note and missing materials list.
5) Ensure 10_structured/THEMES_ON_HOLD.md is updated.
6) Do NOT mark raw/elements as used (that is S8).

## Updates
- 10_structured/themes/*.md
- 20_context/*.md
- 30_drafts/*.md
- 10_structured/THEMES_ON_HOLD.md
