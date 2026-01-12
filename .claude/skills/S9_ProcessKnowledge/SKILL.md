---
name: S9_ProcessKnowledge
description: Process a knowledge note from raw paste: generate title/summary/key points, rename file, and update index.
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# S9_ProcessKnowledge

## Goal
- 70_knowledge のRaw pasteから、Summary/Key pointsとファイル名を自動生成する。
- Raw paste本文は改変しない。

## Inputs
- knowledge_path

## Steps
1) Read the knowledge file and extract the Raw paste section.
2) If Raw paste is empty, ask the user to paste content and rerun.
3) Generate a concise title and 3-7 key points from the raw paste.
4) Generate a safe filename slug from the title (lowercase + hyphen, ASCII only).
   - If the slug is empty or already exists, propose 2-3 alternatives.
   - If still ambiguous, fall back to knowledge-YYYYMMDD-### after user approval.
5) Update the knowledge file:
   - Set H1 to the title.
   - Fill Summary and Key points.
   - Keep Raw paste unchanged.
   - Update frontmatter updated; ensure id exists (knowledge-YYYYMMDD-###).
6) Rename/move the file to 70_knowledge/<slug>.md.
7) Update 70_knowledge/KNOWLEDGE_INDEX.md with a link to the processed file (if missing).

## Updates
- 70_knowledge/*.md
- 70_knowledge/KNOWLEDGE_INDEX.md
