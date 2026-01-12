---
description: Process a knowledge note (generate title/summary/key points, rename file, update index).
---

# /knowledge-process

## Purpose
Process a deep research knowledge note after the user pasted content.

## Inputs
- $ARGUMENTS: knowledge file path (required). If missing, ask the user.

## Steps
1) Get target knowledge file path.
2) Run S9_ProcessKnowledge.

## Updates
- 70_knowledge/*.md
- 70_knowledge/KNOWLEDGE_INDEX.md
