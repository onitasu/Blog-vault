---
name: S6_WriteDraft
description: Write a blog draft in the fixed executive tone using the context file, leaving traceable internal references.
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
---

# S6_WriteDraft

## Goal
- 30_drafts/ にドラフトを作成。
- theme/element/raw/knowledge 参照を残し、後から追跡できるようにする。

## Inputs
- context_file_path
- thesis_statement

## Steps
1) Determine slug from theme title (safe lowercase and underscore).
2) Create draft file:
   - 30_drafts/<date>_<slug>.md using 90_templates/draft.md.
3) Fill:
   - TL;DR
   - Body with headings
   - Action items
   - References (internal links + knowledge links + URLs)
4) Finish by telling the user:
   - "Review in Obsidian"
   - "If ready run /blog-finalize <draft-path> else /blog-hold <draft-path>"

## Updates
- 30_drafts/<date>_<slug>.md
