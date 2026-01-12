---
description: Start a user-initiated article from a topic, while still processing today's raw and building context.
---

# /blog-start

## Purpose
Start a user-initiated article from a given topic, but still process today's raw and build context.

## Inputs
- $ARGUMENTS: topic (required). If missing, ask the user.
- target date (optional). If missing, ask the user (default: today).

## Steps
1) Determine topic and target date.
2) Run skills in order:
   - S1_IngestDailyRaw
   - S2_DistillRawToElementsAndThemes
   - S10_StartFromTopic (create/select theme from the topic)
   - S4_BuildContextFile (include knowledge + WebSearch/WebFetch)
   - S5_ConfirmMainClaim (main claim only)
   - S6_WriteDraft
3) Tell the user to review the draft in Obsidian and choose next action:
   - If ready: /blog-finalize <draft-path>
   - If not enough content: /blog-hold <draft-path>

## Updates
- 00_daily_raw/YYYY-MM-DD.md
- 00_daily_raw/RAW_UNUSED.md
- 10_structured/* indexes and notes
- 20_context/*.md
- 30_drafts/*.md
- 99_logs/processed_raw_ids.md
