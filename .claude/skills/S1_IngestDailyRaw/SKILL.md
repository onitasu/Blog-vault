---
name: S1_IngestDailyRaw
description: Add stable block IDs to today's raw bullets and update RAW_UNUSED without rewriting raw content.
allowed-tools:
  - Read
  - Edit
  - Write
  - Grep
  - Glob
  - AskUserQuestion
---

# S1_IngestDailyRaw

## Goal
- Rawノート（00_daily_raw/YYYY-MM-DD.md）を追跡可能にする。
- 内容は改変しない。許可される編集は行末へのブロックID追加のみ。

## Inputs
- target_date (YYYY-MM-DD). If not provided, ask the user.

## Steps
1) Open 00_daily_raw/<target_date>.md.
2) If 00_daily_raw/<next_date>.md does not exist, create it from 90_templates/daily_raw.md and replace {{YYYY-MM-DD}} with <next_date>.
3) For each raw bullet line, ensure a block id exists:
   - Format: ^raw-YYYYMMDD-###
   - Append with at least one preceding space.
   - Only append; do not reorder, paraphrase, or delete.
4) Update 00_daily_raw/RAW_UNUSED.md:
   - For each newly discovered raw block id not present in RAW_UNUSED or RAW_USED,
     append a line:
     - ![[00_daily_raw/<target_date>#^raw-YYYYMMDD-###]]
5) Do not move anything to RAW_USED here (that is S8 only).
6) Report how many IDs were added, how many new blocks were indexed, and whether the next-day file was created.

## Updates
- 00_daily_raw/<target_date>.md
- 00_daily_raw/RAW_UNUSED.md
