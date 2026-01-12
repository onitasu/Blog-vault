# Claude Code Implementation Instruction  
(Obsidian × Blog OS × Thinking OS)

## あなたの役割
あなた（Claude Code）は、このリポジトリを対象に  
**「思考整理＋毎日1ブログ生成OS」** を実装するエージェントです。

本プロジェクトは以下を満たす必要があります：

- Obsidian Vault 上で完結
- raw → structured → context → draft → ready → thinking の循環
- AI主導・人間は選択と承認のみ
- すべて追跡可能（raw / element / theme / article / thinking）

---

## 参照すべき要件
以下の要件ファイルを **必ず最初に全文読み、設計判断の根拠にしてください**。

- docs/requirements.md  
  ※ このファイルが Single Source of Truth です  
  ※ 要件に反する実装は禁止です

---

## 実装ゴール（最終状態）

このVaultで以下が可能になること：

1. iPhoneで raw を追記するだけでよい
2. 朝 `/blog-morning` を実行すると：
   - raw に block id が付与され
   - raw → elements / themes が整理され
   - 新規テーマ＋保留テーマ再開を含めた記事候補が提示され
   - 選択後、context（内部参照＋Web調査）がファイル化され
   - 記事の「主張」だけを確認され
   - draft が生成される
3. `/blog-finalize <draft>` を実行すると：
   - Ready 化
   - raw / elements / themes の unused → used 移行
   - thinking 抽出と更新（ユーザー承認付き）
   が **必ず同時に** 行われる
4. `/blog-start <topic>` を実行すると：
   - 当日の raw 処理（S1/S2）が走り
   - topic起点でテーマが作成/選択され
   - context → 主張確認 → draft が生成される

---

## 実装方針（重要）

### 1. Rawは非破壊
- raw本文の言い換え・要約・並び替えは禁止
- 許可される編集は：
  - 行末への block id（^raw-YYYYMMDD-###）の追加のみ

### 2. 状態管理は「移動」ではなく「status」
- theme / element ノートは **移動しない**
- status: unused | on_hold | used を frontmatter で管理
- 一覧ファイル（THEMES_UNUSED.md 等）を常に更新する

### 3. 相互参照は Obsidian 標準記法を使う
- ノートリンク： [[path/to/note]]
- ブロック参照： [[file#^blockid]]
- ブロック埋め込み： ![[file#^blockid]]
- これ以外の独自記法は禁止

### 4. S3_ProposeArticle は必ず以下を考慮
- 新規テーマ
- 保留テーマの再開可能性
- 最近追加された elements / raw との親和性
- 提案は AskUserQuestion による選択式

### 5. 意図確認は「主張」だけ
- トーン・文体・想定読者は **固定**
- それらは rules / CLAUDE.md に明示する
- S5 で聞くのは：
  - メインの主張（1文）
  - それを支える主役の要素（選択式）

### 6. Finalize は必ず一括処理
- S8 / S9 / S10 に相当する処理は
  **ユーザー操作上は1アクション**
- 内部的に分割してもよいが：
  - raw unused → used
  - element/theme unused → used
  - thinking 抽出提案 → 承認 → 反映
  が必ず同時に実行されること

---

## 実装対象（作るべきもの）

### A. Claude Code 基盤
- CLAUDE.md（プロジェクト常駐指示）
- .claude/rules/*.md（文体・運用ルール）
- .claude/commands/
  - blog-morning.md
  - blog-start.md
  - blog-finalize.md
  - blog-hold.md
  - knowledge-process.md
- .claude/skills/
  - S1_IngestDailyRaw
  - S2_DistillRawToElementsAndThemes
  - S3_ProposeArticle
  - S4_BuildContextFile
  - S5_ConfirmMainClaim
  - S6_WriteDraft
  - S7_PutOnHold
  - S8_FinalizeAndArchive
  - S9_ProcessKnowledge
  - S10_StartFromTopic

### B. Obsidian 側テンプレ
- 90_templates/
  - daily_raw.md
  - element.md
  - theme.md
  - context.md
  - draft.md
  - thinking.md
  - knowledge.md

### C. 一覧・管理ファイル
- RAW_UNUSED.md / RAW_USED.md
- THEMES_UNUSED.md / THEMES_ON_HOLD.md / THEMES_USED.md
- ELEMENTS_UNUSED.md / ELEMENTS_USED.md
- READY_INDEX.md
- THINKING_INDEX.md
- KNOWLEDGE_INDEX.md
- 99_logs/blog_os_log.md
- 99_logs/processed_raw_ids.md

---

## Claude Code に求める振る舞い

- 基本は **自律的に次の作業を提案**
- ユーザーには常に：
  - 選択肢
  - 明確な /command
  を提示する
- ユーザーが「次何すればいい？」と考えなくてよい状態を作る

---

## 実装手順（Claude Codeが行う）

1. requirements.md を読み、前提を内部メモリに要約
2. フォルダ構造を確認し、なければ作成
3. CLAUDE.md を生成
4. rules → commands → skills → templates の順で生成
5. 各 Skill / Command は：
   - 目的
   - 入力
   - 処理手順
   - 更新するファイル
   が明確になるよう記述
6. 最後に：
   - `/blog-morning` 実行例
   - `/blog-finalize` 実行例
   を README 形式で簡単に提示

---

## 重要な制約
- 要件にない機能を勝手に追加しない
- 「便利そうだから」という理由で設計を変えない
- 迷ったら必ず requirements.md に立ち返る

---

## 完了条件
- この Vault 上で、要件どおりの Blog OS が実行可能
- ユーザーは raw 記述と選択・承認だけで回せる
- 全ての思考・記事・要素が Obsidian 内で追跡可能
