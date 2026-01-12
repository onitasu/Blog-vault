---
name: S10_StartFromTopic
description: Create or select a theme from a user-provided topic and link relevant elements, then update indexes.
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# S10_StartFromTopic

## Goal
- ユーザー起点のテーマを作成または既存テーマを選択し、関連要素と相互参照を作る。

## Inputs
- topic (required)
- target_date (YYYY-MM-DD)

## Steps
1) Search existing theme notes by filename/title for matches to the topic.
2) If matches are found, ask the user to:
   - Use an existing theme, or
   - Create a new theme from the topic.
3) If creating a new theme:
   - Generate a new theme id (theme-YYYYMMDD-###).
   - Create 10_structured/themes/theme-YYYYMMDD-###.md using 90_templates/theme.md.
   - Set title to the topic and status to unused.
4) Link relevant elements:
   - Scan recent elements (target_date and nearby days) and match by keywords.
   - Add matched elements to the theme note.
   - Update each element note's Related themes to include the theme.
5) Update index files:
   - THEMES_UNUSED / THEMES_ON_HOLD / THEMES_USED
   - ELEMENTS_UNUSED / ELEMENTS_USED (if element status changed)

## Output
- theme_id and theme file path

## Updates
- 10_structured/themes/*.md
- 10_structured/elements/*.md
- 10_structured/* index files
