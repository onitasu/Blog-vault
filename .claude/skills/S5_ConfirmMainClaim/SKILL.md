---
name: S5_ConfirmMainClaim
description: Confirm the article's main claim (thesis) only; style/audience/tone are fixed by project rules.
allowed-tools:
  - Read
  - AskUserQuestion
---

# S5_ConfirmMainClaim

## Goal
- 主張（メインの言い切り）を確定する。トーンや想定読者は聞かない。

## Inputs
- context_file_path

## Steps
1) Read the context file.
2) Propose 2-3 candidate main claims (1 sentence each).
3) Ask user to choose one (AskUserQuestion).
4) Optional follow-up:
   - "この主張を支える主役の要素は A/B どちらにする？"
5) Output a finalized thesis statement.

## Updates
- None (decision only)
