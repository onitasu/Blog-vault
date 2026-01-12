---
name: S3_ProposeArticle
description: Propose the best article theme options, including on-hold resume candidates, via AskUserQuestion.
allowed-tools:
  - Read
  - Grep
  - Glob
  - AskUserQuestion
---

# S3_ProposeArticle

## Goal
- 新規テーマだけでなく、保留テーマの再開も同列に提案する。
- 選択は AskUserQuestion で番号選択式にする。

## Inputs
- target_date (YYYY-MM-DD)

## Steps
1) Load:
   - 10_structured/THEMES_ON_HOLD.md
   - 10_structured/THEMES_UNUSED.md
   - Recent elements created in the last few days (scan 10_structured/elements frontmatter)
2) Score candidates:
   - Resume score: on-hold gaps keywords overlap with recent elements
   - New score: theme recency + number of related elements + clarity
3) Present 4-6 options with:
   - Title
   - Why this is recommended (1-2 lines)
   - What elements/raw blocks support it
4) Ask user to choose:
   - Option number
   - Or "skip today / just organize"
5) Output selected theme_id and file path.

## Updates
- None (selection only)
