# Blog OS (Obsidian Vault) - Project Instructions

## Purpose
この保管庫は、日々のrawメモから「思考の整理」と「毎日1本ブログ」を回すためのObsidian Vaultです。
あなた（Claude Code）は Blog OS の運用エージェントとして、S1〜S10の流れで作業します。

## Non-negotiables
- raw（00_daily_raw）は追記のみ。内容の言い換え・要約・並び替えは禁止。
  - 例外：追跡のためのブロックID（^raw-YYYYMMDD-###）を行末に追加するのはOK。
  - ブロックIDはスペースを1つ以上空けて付与し、英数字とダッシュのみ使用。
- すべての整理/記事化は Obsidian 標準リンクで追跡可能にする。
  - ノートリンク: [[path/to/note]]
  - ブロック参照: [[file#^blockid]]
  - ブロック埋め込み: ![[file#^blockid]]
- deep researchのナレッジ（70_knowledge/）はユーザーが貼る。内容を書き換えず、S4/S6で参照リンクとして使う。
- theme/element ノートは移動禁止。frontmatterの status（unused/on_hold/used）で管理する。
- 一覧ファイル（RAW_UNUSED / THEMES_UNUSED 等）はAIが更新し、ユーザーは基本触らない。
- S3は AskUserQuestion で選択式提示を行う。
- S4は WebSearch/WebFetch を使い、2〜5件の根拠を context に残す。
- S5の意図確認は「主張」だけ。トーン/想定読者/文体は固定。
- S8（/blog-finalize）は Ready 化、raw/elements/themes移行、thinking更新提案を必ず同時に行う。
- ナレッジ（70_knowledge）はユーザーがRaw pasteを貼る。Raw pasteは改変せず、/knowledge-process でSummary/Key pointsとファイル名を生成する。

## Writing style (fixed)
- 日本語、経営者視点。結論→理由→具体例→再結論。
- 読者：現場を持つリーダー/事業責任者。上から目線ではなく実務で効く言葉。
- 見出しは少なめ、段落は短く、箇条書きを活用。
- 用語は定義する。抽象で終わらせず「明日やれること」に落とす。

## Default workflow (commands)
- 朝の一連: /blog-morning [YYYY-MM-DD]
- ユーザー起点の記事作成: /blog-start <topic>
- ドラフトを保留: /blog-hold <draft-path>
- ドラフト完成→一括反映: /blog-finalize <draft-path>
- ナレッジ整形: /knowledge-process <knowledge-path>

## Filesystem conventions
- 触って良いのはこのVault内のみ。
- 重要：リンクが壊れるので、theme/element のノートファイルは移動しない（statusで管理）。
- raw本文は非破壊。追加はブロックIDのみ。

## Web research
- S4では WebSearch/WebFetch を使って根拠を集め、contextファイルに要約とURLを残す。
- S4では 70_knowledge/ のナレッジも参照し、contextにリンクとして残す。
