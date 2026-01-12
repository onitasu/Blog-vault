---
name: S8_FinalizeAndArchive
description: Finalize a draft into Ready and update tracking: raw unused->used, elements/themes status, thinking extraction proposal with user approval, and logs.
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# S8_FinalizeAndArchive

## Goal
ドラフト完成時に必ず同時に行う:
1) Ready化（40_ready）
2) raw unused->used 移行
3) elements/themes を used に更新
4) 思考整理（thinkingファイルへの追記）を提案し、承認後に反映
5) ログ記録

## Inputs
- draft_path

## Steps
1) Read draft, identify:
   - theme note link
   - element note links
   - raw block embeds
2) Create/Update Ready:
   - Copy draft content into 40_ready/<same-name>.md
   - Update frontmatter status: ready
   - Update 40_ready/READY_INDEX.md
3) Update statuses:
   - theme status -> used
   - element status -> used (only those referenced)
   - Update THEMES_USED / ELEMENTS_USED indexes
4) Raw migration:
   - For each used raw block id:
     - Remove its embed line from RAW_UNUSED.md (if present)
     - Append it to RAW_USED.md (if not present)
5) Thinking extraction (requires user approval):
   - Propose 3-7 essence bullets with suggested target thinking file(s)
   - Ask user to approve (all / partial / edit targets)
   - Apply edits to 60_thinking/*.md
   - Each essence must include a backlink to the Ready article and the date
6) Append a summary record to 99_logs/blog_os_log.md

## Updates
- 40_ready/*.md and 40_ready/READY_INDEX.md
- 00_daily_raw/RAW_UNUSED.md and 00_daily_raw/RAW_USED.md
- 10_structured/themes/*.md and 10_structured/elements/*.md
- 10_structured/THEMES_USED.md and 10_structured/ELEMENTS_USED.md
- 60_thinking/*.md and 60_thinking/THINKING_INDEX.md
- 99_logs/blog_os_log.md
