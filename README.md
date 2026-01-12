# Blog OS (Obsidian Vault)

このVaultは、Obsidianと併用し、rawメモから「思考の整理」と「毎日1本ブログ」を回すためのBlog OSです。  
スマホ（iPhone）と同期して、日常メモをiPhoneから追記できます。  
ユーザーは **raw記述・選択・承認** のみを行い、整理/記事化はClaude Codeが進めます。

## 主要コマンド

- `/blog-morning`（日付は省略可）  
  朝の一連（raw→整理→提案→context→主張確認→draft）
- `/blog-start <topic>`  
  ユーザー起点で記事化（当日のraw処理も同時に実行）
- `/blog-finalize <draft-path>`  
  draft→Ready化＋raw/elements/themes移行＋thinking更新提案（同時実行）
- `/blog-hold <draft-path>`  
  保留化（不足材料を記録し、再提案候補に）
- `/knowledge-process <knowledge-path>`  
  deep research貼り付け後にSummary/Key pointsとファイル名を生成

## 日々の運用フロー

### 日中（随時）
- `00_daily_raw/YYYY-MM-DD.md` に **1行＝1メモ** で追記

### deep research を貼った日
- `70_knowledge/<title>.md` を作成しRaw pasteに貼り付け
- `/knowledge-process 70_knowledge/<title>.md`

### 毎朝（記事を書く時間）
1. `/blog-morning YYYY-MM-DD`
2. 提案から選択
3. context → 主張確認 → draft まで自動生成
4. 確認後、必要に応じて:
   - OKなら `/blog-finalize 30_drafts/<file>.md`
   - 足りなければ `/blog-hold 30_drafts/<file>.md`

## ユーザー起点のフロー（テーマが最初からある日）

1. `/blog-start "<topic>"`
2. 当日のraw処理（S1/S2）が走る
3. topic起点のテーマ作成/選択 → context → 主張確認 → draft
4. 以降は `/blog-finalize` or `/blog-hold`

## knowledge運用のポイント

- ファイル名はタイトルと一致させる（例: `decision-principles.md`）
- `id` はユニークID（例: `knowledge-YYYYMMDD-###`）
- Raw paste本文はAIが改変しない
- 参照はファイル名ベース（例: `[[70_knowledge/decision-principles]]`）

## 重要ルール（抜粋）

- raw本文は **非破壊**（追記のみ、ブロックID追加のみ許可）
- 相互参照は Obsidian 標準記法のみ（`[[...]]` / `[[file#^id]]` / `![[file#^id]]`）
- theme/elementは **移動しない**（statusで管理）
- S4は knowledge + Web調査をcontextへ記録

## 参考ドキュメント

- `docs/requirements.md`（Single Source of Truth）
- `docs/IMPLEMENTATION_INSTRUCTION.md`
- `docs/REFERENCE_LINKS.md`
