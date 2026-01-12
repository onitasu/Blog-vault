---
description: Blog OS morning routine. Ingest raw -> distill -> propose theme -> build context (knowledge + web) -> confirm main claim -> write draft.
---

# /blog-morning

## Purpose
Run the full morning workflow from raw ingestion to draft creation.

## Inputs
- $ARGUMENTS: YYYY-MM-DD (optional). If missing, use today by default.

## Steps
1) Determine target date:
   - If $ARGUMENTS is provided, use it as YYYY-MM-DD.
   - Otherwise, use today's date. Ask only if the date cannot be determined.
2) Run skills in order:
   - S1_IngestDailyRaw
   - S2_DistillRawToElementsAndThemes
   - S3_ProposeArticle (use AskUserQuestion for selection)
   - S4_BuildContextFile (after theme selection; include knowledge + WebSearch/WebFetch)
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
