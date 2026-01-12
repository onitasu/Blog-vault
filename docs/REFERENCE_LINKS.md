# Reference Links for Implementation  
(Claude Code × Obsidian Blog/Thinking OS)

このファイルは **実装時に必ず参照すべき公式ドキュメント集** です。  
Claude Code は、以下のリンク内容を前提に **記法・API・制約を厳密に守って実装してください**。

---

## 1. Claude Code（最重要）

### ■ Claude Code Overview（公式）
https://code.claude.com/docs/ja/overview

- Claude Code の全体像
- プロジェクト構成
- `CLAUDE.md` / `.claude/` の考え方

---

### ■ Project Memory / CLAUDE.md
https://code.claude.com/docs/ja/project-memory

- `CLAUDE.md` の役割
- 起動時に自動で読み込まれる指示
- rules 分割の考え方

👉 **本プロジェクトでは、必ず CLAUDE.md + .claude/rules を使用すること**

---

### ■ Custom Slash Commands
https://code.claude.com/docs/ja/slash-commands

- `.claude/commands/*.md` の仕様
- `$ARGUMENTS` の扱い
- description フロントマター

👉 `/blog-morning`, `/blog-finalize`, `/blog-hold` はこの仕様に準拠すること

---

### ■ Claude Code Skills（Agents）
https://code.claude.com/docs/ja/skills

- `.claude/skills/<name>/SKILL.md` の構造
- `name`, `description`, `allowed-tools`
- Skills が “自律実行単位” であること

👉 S1〜S8 の Skill は **この仕様を厳守**

---

### ■ Tools / AskUserQuestion / WebSearch
https://code.claude.com/docs/ja/tools

- AskUserQuestion（選択式質問）
- WebSearch / WebFetch
- Read / Write / Edit / Grep / Glob

👉  
- 記事テーマ選択（S3）は **AskUserQuestion**
- Context 構築（S4）は **WebSearch/WebFetch** を使用すること

---

## 2. Obsidian（記法・リンクの正確性が必須）

### ■ 内部リンク（ノート・見出し）
https://help.obsidian.md/Linking+notes+and+files/Internal+links

- `[[ノート名]]`
- `[[ノート名#見出し]]`

👉 **これ以外の独自リンク記法は禁止**

---

### ■ ブロック参照・埋め込み（超重要）
https://help.obsidian.md/Linking+notes+and+files/Link+to+blocks

- `[[file#^blockid]]`
- `![[file#^blockid]]`
- ブロックIDの付け方

👉  
- raw の 1行 = 1 block  
- `^raw-YYYYMMDD-###` 形式で付与すること

---

### ■ トランスクルージョン（埋め込み）
https://help.obsidian.md/Linking+notes+and+files/Embed+files

- `![[...]]` の意味
- 元ファイルが Single Source of Truth であること

👉 raw / element / theme の追跡は **必ず埋め込みで行う**

---

### ■ Frontmatter（YAML）
https://help.obsidian.md/Editing+and+formatting/Properties

- `---` で囲む
- status / created / updated の管理

👉 theme / element / draft / context は **必ず frontmatter を持つ**

---

## 3. 設計上の重要ルール（再掲）

Claude Code は、以下を **ドキュメント仕様として厳守** すること。

### Raw
- raw本文は書き換え禁止
- 許可：行末への block id 追加のみ

### Theme / Element
- ファイル移動は禁止
- status: unused | on_hold | used で管理
- 相互参照は Obsidian 標準リンクのみ

### 記事生成
- 意図確認は「主張」のみ
- トーン・想定読者・文体は固定（CLAUDE.md / rules に従う）

### Finalize
- raw / element / theme / thinking の更新は **必ず同時**
- ユーザー操作は 1 コマンドのみ

---

## 4. 実装時の判断基準

- 仕様が曖昧な場合：
  1. requirements.md
  2. IMPLEMENTATION_INSTRUCTION.md
  3. この Reference Links
の **優先順位で解釈すること**

- 「便利そう」「一般的だから」という理由での逸脱は禁止

---

## 5. 完了条件（再掲）

- Skills / Commands / Templates が公式仕様に完全準拠
- Obsidian 上ですべての参照が壊れない
- Blog OS が **AI主導で自律的に進む**
- ユーザーは選択と承認だけで良い
