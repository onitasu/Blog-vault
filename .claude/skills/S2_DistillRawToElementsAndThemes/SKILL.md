---
name: S2_DistillRawToElementsAndThemes
description: Convert new raw blocks into element/theme notes and update mutual links plus index files.
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
---

# S2_DistillRawToElementsAndThemes

## Goal
- 新規rawブロック（未処理）を element/theme に整理し、相互参照を必ず作る。
- raw本文は改変しない（S1でID付与したもの以外は触らない）。
- unused/used/on_hold の一覧ファイルを更新して現状を可視化する。

## Inputs
- target_date (YYYY-MM-DD)
- Source of truth:
  - 00_daily_raw/RAW_UNUSED.md
  - 99_logs/processed_raw_ids.md

## Steps
1) Load 99_logs/processed_raw_ids.md and build a set of processed raw IDs.
2) From RAW_UNUSED.md, identify raw block embeds for the target_date.
3) For each raw block id not yet processed:
   a) Create an element note in 10_structured/elements/elem-YYYYMMDD-###.md using 90_templates/element.md.
   b) Embed the raw block in the element note:
      - ![[00_daily_raw/<date>#^raw-...]]
   c) Suggest/assign 1-3 candidate themes:
      - Link to existing theme notes when possible, or create a new theme note using 90_templates/theme.md.
   d) Update the theme note to link back to the element note.
4) Append processed raw IDs to 99_logs/processed_raw_ids.md (append-only).
5) Rebuild/update index files (read frontmatter status; do not rely on plugins):
   - 10_structured/ELEMENTS_UNUSED.md
   - 10_structured/ELEMENTS_USED.md
   - 10_structured/THEMES_UNUSED.md
   - 10_structured/THEMES_ON_HOLD.md
   - 10_structured/THEMES_USED.md

## Updates
- 10_structured/elements/*.md
- 10_structured/themes/*.md
- 99_logs/processed_raw_ids.md
- 10_structured/* index files
