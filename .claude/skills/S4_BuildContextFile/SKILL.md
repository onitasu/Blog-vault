---
name: S4_BuildContextFile
description: Create a context file with direction, internal references, knowledge, and web research notes for the selected theme.
allowed-tools:
  - Read
  - Write
  - Edit
  - WebSearch
  - WebFetch
  - Grep
  - Glob
---

# S4_BuildContextFile

## Goal
- 方向性・内部参照（theme/element/raw）・ナレッジ（deep research）・Web調査を1ファイルにまとめる。

## Inputs
- theme_id (required)
- target_date (YYYY-MM-DD)

## Steps
1) Read the theme note, linked element notes, and relevant knowledge notes in 70_knowledge/ (match by theme title, keywords, or tags).
2) Create 20_context/ctx-<date>-<theme_id>.md using 90_templates/context.md.
3) Knowledge:
   - Add relevant knowledge links from 70_knowledge/ (do not rewrite the knowledge content).
4) Web research:
   - Use WebSearch for 2-5 high quality sources relevant to the theme.
   - Use WebFetch to extract key points.
   - Save summaries + URLs into the context file.
5) Identify "gaps" that may cause draft to be on-hold.

## Updates
- 20_context/ctx-<date>-<theme_id>.md
