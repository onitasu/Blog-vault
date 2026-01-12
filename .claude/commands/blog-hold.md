---
description: Put a draft/theme on hold, record missing parts, and ensure it will be suggested for resume later.
---

# /blog-hold

## Purpose
Mark a draft/theme/context as on-hold and record missing materials.

## Inputs
- $ARGUMENTS: draft file path (required). If missing, ask the user.

## Steps
1) Get target draft path.
2) Run S7_PutOnHold.

## Updates
- 10_structured/themes/*.md (status: on_hold)
- 20_context/*.md (status: on_hold)
- 30_drafts/*.md (on-hold notes)
- 10_structured/THEMES_ON_HOLD.md
