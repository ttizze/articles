---
saved_at: "2026-03-19T06:39:04.176Z"
source_url: "https://x.com/affaanmustafa/status/2012378465664745795?s=12"
source_app: "ios-share-extension"
page_title: "The Shorthand Guide to Everything Claude Code"
note: ""
content_type: "application/x-x-article+plain"
extractor: "x-graphql-article"
---

> # The Shorthand Guide to Everything Claude Code
# Claude Codeのすべてを網羅したショートハンドガイド

> ![Cover image](assets/img-01-G-1nccYaoAATrW2.jpg)

> Here's my complete setup after 10 months of daily use: skills, hooks, subagents, MCPs, plugins, and what actually works.
10ヶ月間の毎日の使用を経た、私の完全なセットアップを紹介します：スキル、フック、サブエージェント、MCP、プラグイン、そして実際に機能するものについて。

> Been an avid Claude Code user since the experimental rollout in Feb, and won the Anthropic x Forum Ventures hackathon with Zenith alongside @DRodriguezFX completely using Claude Code.
2月の実験的なロールアウト以来、Claude Codeの熱心なユーザーで、@DRodriguezFXと共にZenithとしてAnthropicとForum Venturesのハッカソンを完全にClaude Codeを使用して優勝しました。

> Skills and Commands
スキルとコマンド

> Skills operate like rules, constricted to certain scopes and workflows. They're shorthand to prompts when you need to execute a particular workflow.
スキルはルールのように機能し、特定のスコープとワークフローに制限されています。特定のワークフローを実行する必要があるときのプロンプトのショートハンドです。

> After a long session of coding with Opus 4.5, you want to clean out dead code and loose .md files?
Opus 4.5での長いコーディングセッションの後、デッドコードや不要な.mdファイルをクリーンアップしたいですか？

> Run /refactor-clean. Need testing? /tdd, /e2e, /test-coverage. Skills and commands can be chained together in a single prompt
/refactor-cleanを実行してください。テストが必要ですか？ /tdd、/e2e、/test-coverage。スキルとコマンドは1つのプロンプトで連鎖させることができます。

> I can make a skill that updates codemaps at checkpoints - a way for Claude to quickly navigate your codebase without burning context on exploration.
チェックポイントでコードマップを更新するスキルを作成できます。これはClaudeが探索でコンテキストを消費せずにコードベースを素早くナビゲートする方法です。

> ~/.claude/skills/codemap-updater.md

> Commands are skills executed via slash commands. They overlap but are stored differently:
コマンドはスラッシュコマンドを介して実行されるスキルです。重複していますが、異なる場所に保存されます：

> Skills: ~/.claude/skills - broader workflow definitions
> Commands: ~/.claude/commands - quick executable prompts
- スキル：~/.claude/skills - より広いワークフロー定義
- コマンド：~/.claude/commands - クイック実行可能プロンプト

> Hooks
フック

> Hooks are trigger-based automations that fire on specific events. Unlike skills, they're constricted to tool calls and lifecycle events.
フックは特定のイベントで発火するトリガーベースの自動化です。スキルとは異なり、ツールコールとライフサイクルイベントに制限されています。

> Hook Types
フックの種類

> PreToolUse  - Before a tool executes (validation, reminders)
> PostToolUse - After a tool finishes (formatting, feedback loops)
> UserPromptSubmit - When you send a message
> Stop - When Claude finishes responding
> PreCompact - Before context compaction
> Notification - Permission requests
- PreToolUse - ツールが実行される前（検証、リマインダー）
- PostToolUse - ツールが完了した後（フォーマット、フィードバックループ）
- UserPromptSubmit - メッセージを送信したとき
- Stop - Claudeが応答を終了したとき
- PreCompact - コンテキスト圧縮の前
- Notification - 権限リクエスト

> Example: tmux reminder before long-running commands
例：長時間実行コマンドの前のtmuxリマインダー

> Pro tip: Use the `hookify` plugin to create hooks conversationally instead of writing JSON manually. Run /hookify and describe what you want.
プロのヒント：JSONを手動で書く代わりに、`hookify`プラグインを使って会話形式でフックを作成しましょう。/hookifyを実行して、やりたいことを説明してください。

> Subagents
サブエージェント

> Subagents are processes your orchestrator (main Claude) can delegate tasks to with limited scopes. They can run in background or foreground, freeing up context for the main agent.
サブエージェントは、オーケストレーター（メインのClaude）が限定されたスコープでタスクを委任できるプロセスです。バックグラウンドまたはフォアグラウンドで実行でき、メインエージェントのコンテキストを解放します。

> Subagents work nicely with skills - a subagent capable of executing a subset of your skills can be delegated tasks and use those skills autonomously. They can also be sandboxed with specific tool permissions.
サブエージェントはスキルとうまく連携します。スキルのサブセットを実行できるサブエージェントはタスクを委任され、それらのスキルを自律的に使用できます。また、特定のツール権限でサンドボックス化することもできます。

> Configure allowed tools, MCPs, and permissions per subagent for proper scoping.
適切なスコーピングのため、サブエージェントごとに許可するツール、MCP、権限を設定してください。

> Rules and Memory
ルールとメモリ

> Your `.rules` folder holds `.md` files with best practices Claude should ALWAYS follow. Two approaches:
`.rules`フォルダには、Claudeが常に従うべきベストプラクティスを記載した`.md`ファイルが格納されています。2つのアプローチがあります：

> Single CLAUDE.md - Everything in one file (user or project level)
> Rules folder - Modular `.md` files grouped by concern
- 単一のCLAUDE.md - すべてを1つのファイルにまとめる（ユーザーまたはプロジェクトレベル）
- Rulesフォルダ - 関心事ごとにグループ化されたモジュール式`.md`ファイル

> Example rules:
ルールの例：

> No emojis in codebase
> Refrain from purple hues in frontend
> Always test code before deployment
> Prioritize modular code over mega-files
> Never commit console.logs
- コードベースに絵文字を使わない
- フロントエンドで紫色のトーンを避ける
- デプロイ前に必ずコードをテストする
- 大規模ファイルよりもモジュール式コードを優先する
- console.logsをコミットしない

> MCPs (Model Context Protocol)
MCP（モデルコンテキストプロトコル）

> MCPs connect Claude to external services directly. Not a replacement for APIs - it's a prompt-driven wrapper around them, allowing more flexibility in navigating information.
MCPはClaudeを外部サービスに直接接続します。APIの代替ではなく、プロンプト駆動のラッパーで、情報のナビゲーションにより柔軟性をもたらします。

> Example: Supabase MCP lets Claude pull specific data, run SQL directly upstream without copy-paste. Same for databases, deployment platforms, etc.
例：Supabase MCPを使用すると、Claudeはコピー&ペーストなしで特定のデータを取得し、SQLを直接上流で実行できます。データベース、デプロイメントプラットフォームなども同様です。

> Chrome in Claude: is a built-in plugin MCP that lets Claude autonomously control your browser - clicking around to see how things work.
Claude内のChrome：Claudeがブラウザを自律的に操作できる組み込みプラグインMCPです。動作確認のためにクリックして操作します。

> CRITICAL: Context Window Management
重要：コンテキストウィンドウの管理

> Be picky with MCPs. I keep all MCPs in user config but disable everything unused. Navigate to /plugins and scroll down or run /mcp.
MCPには選択的に。すべてのMCPをユーザー設定に保持しますが、未使用のものはすべて無効にします。/pluginsに移動してスクロールするか、/mcpを実行してください。

> Your 200k context window before compacting might only be 70k with too many tools enabled. Performance degrades significantly.
圧縮前の200kコンテキストウィンドウは、ツールを有効にしすぎると70kにしかならない場合があります。パフォーマンスが大幅に低下します。

> Rule of thumb: Have 20-30 MCPs in config, but keep under 10 enabled / under 80 tools active.
目安：設定には20〜30のMCPを持ちますが、有効にするのは10未満、アクティブなツールは80未満にしてください。

> Plugins
プラグイン

> Plugins package tools for easy installation instead of tedious manual setup. A plugin can be a skill + MCP combined, or hooks/tools bundled together.
プラグインは、面倒な手動セットアップの代わりに、簡単にインストールできるようにツールをパッケージ化します。プラグインはスキルとMCPを組み合わせたもの、またはフック/ツールをまとめたものにできます。

> Installing plugins:
プラグインのインストール：

> LSP Plugins: are particularly useful if you run Claude Code outside editors frequently. Language Server Protocol gives Claude real-time type checking, go-to-definition, and intelligent completions without needing an IDE open.
LSPプラグイン：エディタの外でClaude Codeを頻繁に実行する場合に特に便利です。言語サーバープロトコルにより、IDEを開かなくてもリアルタイムの型チェック、定義へのジャンプ、インテリジェントな補完機能をClaudeに提供します。

> Same warning as MCPs - watch your context window.
MCPと同じ警告です。コンテキストウィンドウに注意してください。

> Tips and Tricks
ヒントとコツ

> Keyboard Shortcuts
キーボードショートカット

> Ctrl+U - Delete entire line (faster than backspace spam)
> ! - Quick bash command prefix
> @ - Search for files
> / - Initiate slash commands
> Shift+Enter - Multi-line input
> Tab - Toggle thinking display
> Esc Esc - Interrupt Claude / restore code
- Ctrl+U - 行全体を削除（バックスペースの連打より速い）
- ! - クイックbashコマンドプレフィックス
- @ - ファイルを検索
- / - スラッシュコマンドを起動
- Shift+Enter - 複数行入力
- Tab - 思考表示の切り替え
- Esc Esc - Claudeを中断 / コードを復元

> Parallel Workflows
並列ワークフロー

> /fork - Fork conversations to do non-overlapping tasks in parallel instead of spamming queued messages
/fork - キュー待ちのメッセージを送り続けるのではなく、重複しないタスクを並列で行うために会話をフォークする

> Git Worktrees - For overlapping parallel Claudes without conflicts. Each worktree is an independent checkout
Git Worktrees - 競合なしで並列Claudeを重複させるため。各worktreeは独立したチェックアウト

> tmux for Long-Running Commands: Stream and watch logs/bash processes Claude runs.
長時間実行コマンドのtmux：Claudeが実行するログ/bashプロセスをストリームして監視します。

> mgrep > grep: `mgrep` is a significant improvement from ripgrep/grep. Install via plugin marketplace, then use the /mgrep skill. Works with both local search and web search.
mgrep > grep：`mgrep`はripgrep/grepから大幅に改善されています。プラグインマーケットプレイスからインストールし、/mgrepスキルを使用してください。ローカル検索とウェブ検索の両方に対応しています。

> Other Useful Commands
その他の便利なコマンド

> /rewind - Go back to a previous state
> /statusline - Customize with branch, context %, todos
> /checkpoints - File-level undo points
> /compact - Manually trigger context compaction
- /rewind - 前の状態に戻る
- /statusline - ブランチ、コンテキスト%、Todoでカスタマイズ
- /checkpoints - ファイルレベルのアンドゥポイント
- /compact - コンテキスト圧縮を手動でトリガー

> GitHub Actions CI/CD
GitHub Actions CI/CD

> Set up code review on your PRs with GitHub Actions. Claude can review PRs automatically when configured.
GitHub Actionsを使用してPRのコードレビューを設定します。設定すると、ClaudeがPRを自動的にレビューできます。

> Sandboxing
サンドボックス化

> Use sandbox mode for risky operations - Claude runs in restricted environment without affecting your actual system. (Use --dangerously-skip-permissions - to do the opposite of this and let claude roam free, this can be destructive if not careful.)
危険な操作にはサンドボックスモードを使用してください。Claudeは実際のシステムに影響を与えずに制限された環境で実行されます。（--dangerously-skip-permissionsを使用すると逆のことができ、Claudeを自由に動作させることができますが、注意しないと破壊的になる可能性があります。）

> On Editors
エディタについて

> While an editor isn't needed it can positively or negatively impact your Claude Code workflow. While Claude Code works from any terminal, pairing it with a capable editor unlocks real-time file tracking, quick navigation, and integrated command execution.
エディタは必須ではありませんが、Claude Codeのワークフローに良い影響も悪い影響も与える可能性があります。Claude Codeはどのターミナルからでも動作しますが、優れたエディタと組み合わせることで、リアルタイムのファイル追跡、クイックナビゲーション、統合コマンド実行が可能になります。

> Zed (My Preference)
Zed（私の好み）

> I use Zed - a Rust-based editor that's lightweight, fast, and highly customizable.
Zedを使用しています。Rustベースのエディタで、軽量で高速、高度にカスタマイズ可能です。

> Why Zed works well with Claude Code:
ZedがClaude Codeとうまく連携する理由：

> Agent Panel Integration - Zed's Claude integration lets you track file changes in real-time as Claude edits. Jump between files Claude references without leaving the editor
エージェントパネルの統合 - ZedのClaude統合により、Claudeが編集する際のファイル変更をリアルタイムで追跡できます。エディタを離れることなく、Claudeが参照するファイル間をジャンプできます。

> Performance - Written in Rust, opens instantly and handles large codebases without lag
パフォーマンス - Rustで書かれており、即座に開き、大規模なコードベースをラグなく処理します。

> CMD+Shift+R Command Palette - Quick access to all your custom slash commands, debuggers, and tools in a searchable UI. Even if you just want to run a quick command without switching to terminal
CMD+Shift+Rコマンドパレット - 検索可能なUIですべてのカスタムスラッシュコマンド、デバッガー、ツールにすばやくアクセスできます。ターミナルに切り替えずにクイックコマンドを実行したい場合でも便利です。

> Minimal Resource Usage - Won't compete with Claude for system resources during heavy operations
最小限のリソース使用 - 重い操作中もシステムリソースでClaudeと競合しません。

> Vim Mode - Full vim keybindings if that's your thing
Vimモード - お好みであれば、完全なvimキーバインディング

> Split your screen - Terminal with Claude Code on one side, editor on the other using
画面を分割する - 片側にClaude Codeのターミナル、もう一方にエディタを使用

> Ctrl + G  - quickly open the file Claude is currently working on in Zed
Ctrl + G - Claudeが現在作業中のファイルをZedですばやく開く

> Auto-save - Enable autosave so Claude's file reads are always current
自動保存 - 自動保存を有効にして、Claudeのファイル読み取りが常に最新になるようにする

> Git integration - Use editor's git features to review Claude's changes before committing
Git統合 - エディタのgit機能を使用して、コミット前にClaudeの変更をレビューする

> File watchers - Most editors auto-reload changed files, verify this is enabled
ファイルウォッチャー - ほとんどのエディタは変更されたファイルを自動的にリロードします。これが有効になっているか確認してください。

> VSCode / Cursor
VSCode / Cursor

> This is also a viable choice and works well with Claude Code. You can use it in either terminal format, with automatic sync with your editor using \ide enabling LSP functionality (somewhat redundant with plugins now). Or you can opt for the extension which is more integrated with the Editor and has a matching UI.
これも有効な選択肢であり、Claude Codeとうまく連携します。ターミナル形式で使用することも、\ideを使用してエディタと自動同期してLSP機能を有効にすることも（現在はプラグインと若干重複）できます。または、エディタとより統合されたマッチングUIを持つ拡張機能を選択することもできます。

> My Setup
私のセットアップ

> Plugins
プラグイン

> Installed: (I usually only have 4-5 of these enabled at a time)
インストール済み：（通常は4〜5個だけを同時に有効にしています）

> MCP Servers
MCPサーバー

> Configured (User Level):
設定済み（ユーザーレベル）：

> Disabled per project (context window management):
プロジェクトごとに無効（コンテキストウィンドウの管理）：

> This is the key - I have 14 MCPs configured but only ~ 5-6 enabled per project. Keeps context window healthy.
これが重要です。14のMCPを設定していますが、プロジェクトごとに有効にするのは約5〜6個のみです。コンテキストウィンドウを健全に保ちます。

> Key Hooks
主要なフック

> Custom Status Line
カスタムステータスライン

> Shows user, directory, git branch with dirty indicator, context remaining %, model, time, and todo count:
ユーザー、ディレクトリ、ダーティインジケーター付きのgitブランチ、残りコンテキスト%、モデル、時刻、Todoカウントを表示します：

> Rules Structure
ルール構造

> Subagents
サブエージェント

> Key Takeaways
主要なポイント

> Don't overcomplicate - treat configuration like fine-tuning, not architecture
過度に複雑にしない - 設定はアーキテクチャではなくファインチューニングのように扱う

> Context window is precious - disable unused MCPs and plugins
コンテキストウィンドウは貴重です - 未使用のMCPとプラグインを無効にする

> Parallel execution - fork conversations, use git worktrees
並列実行 - 会話をフォークし、git worktreesを使用する

> Automate the repetitive - hooks for formatting, linting, reminders
繰り返し作業を自動化する - フォーマット、リンティング、リマインダーのフック

> Scope your subagents - limited tools = focused execution
サブエージェントをスコープする - 制限されたツール = 集中した実行

> References
参考資料

> - Plugins Reference
> - Hooks Documentation
> - Checkpointing
> - Interactive Mode
> - Memory System
> - [Subagents]
> - [MCP Overview]
- プラグインリファレンス
- フックドキュメント
- チェックポインティング
- インタラクティブモード
- メモリシステム
- [サブエージェント]
- [MCP概要]

> Note: This is a subset of detail. I might make more posts on specifics if people are interested.
注：これは詳細の一部です。興味がある方がいれば、具体的な内容についてさらに投稿するかもしれません。
