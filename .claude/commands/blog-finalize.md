---
description: Finalize a draft into Ready and update tracking (raw/elements/themes + thinking extraction proposal).
---

# /blog-finalize

## Purpose
Finalize a draft in one action: Ready化 + raw/elements/themesの更新 + thinking抽出提案 + logs。

## Inputs
- $ARGUMENTS: draft file path (required). If missing, ask the user to paste the path.

## Steps
1) Get target draft path.
2) Run S8_FinalizeAndArchive.

## Updates
- 40_ready/*.md and 40_ready/READY_INDEX.md
- 00_daily_raw/RAW_UNUSED.md and 00_daily_raw/RAW_USED.md
- 10_structured/* (status updates + index files)
- 60_thinking/*.md and 60_thinking/THINKING_INDEX.md
- 99_logs/blog_os_log.md
