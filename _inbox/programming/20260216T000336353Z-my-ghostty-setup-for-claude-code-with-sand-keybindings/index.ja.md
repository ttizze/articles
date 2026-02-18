---
saved_at: "2026-02-16T00:03:36.353Z"
source_url: "https://x.com/dani_avila7/status/2023151176758268349?s=12"
source_app: "ios-share-extension"
page_title: "My Ghostty setup for Claude Code with SAND Keybindings"
note: ""
content_type: "application/x-x-article+plain"
extractor: "x-graphql-article"
---

> # My Ghostty setup for Claude Code with SAND Keybindings

# Claude Code 向け Ghostty セットアップ（SAND キーバインド付き）

> ![Cover image](assets/img-01-HBOjn6UX0AAQhI.jpg)

> First... Why I Switched to Ghostty

まず……なぜ Ghostty に切り替えたのか

> After months using Claude Code daily I realized I was barely using VSCode or Cursor, just the terminal and git panel, everything else Claude Code handled.

何ヶ月も毎日 Claude Code を使い続けた結果、VSCode や Cursor をほとんど使わず、ターミナルと git パネルだけで事足りていることに気づいた。あとのことは Claude Code が全部やってくれる。

> The problem is VSCode's terminal is fragile, long Claude Code sessions crash it, even on an M4. It's not hardware, it's a terminal not built for AI-scale output... I needed a real terminal

問題は VSCode のターミナルが脆弱なことだ。長い Claude Code セッションはクラッシュさせてしまう。M4 でさえそうだ。ハードウェアの問題ではなく、AI スケールの出力に対応して作られていないターミナルの問題だ……本物のターミナルが必要だった。

> Ghostty came up, community matters and it's built by @mitchellh, co-founder of HashiCorp, someone with a serious track record. Ghostty felt future-proof.

Ghostty が浮上した。コミュニティも重要だし、HashiCorp の共同創業者である @mitchellh が作っており、実績も申し分ない。Ghostty は将来性があると感じた。

> This is the first of three articles about my workflow with Ghostty and Claude Code I start with my "SAND" keybindings that make panel management second nature

これは Ghostty と Claude Code のワークフローについての3本シリーズの第1弾だ。パネル管理を自然に行えるようにする「SAND」キーバインドから始める。

> My Ghostty setup for Claude Code with SAND Keybindings
>
> Monitoring Claude Code changes with Lazygit
>
> Parallel agents with Git worktrees and Claude Code

- Claude Code 向け Ghostty セットアップ（SAND キーバインド付き）
- Lazygit で Claude Code の変更を監視する
- Git ワークツリーと Claude Code で並列エージェントを使う

> Getting Started with Ghostty

Ghostty を使い始める

> Download Ghostty from ghostty.org (macOS and Linux). Once installed, you need a configuration file at ~/.config/ghostty/config.

ghostty.org から Ghostty をダウンロードする（macOS と Linux 対応）。インストールしたら `~/.config/ghostty/config` に設定ファイルが必要だ。

> The easiest way to set it up? Open Claude Code and tell it:

一番簡単なセットアップ方法は？Claude Code を開いて次のように伝える：

> Configure Ghostty with this config: https://gist.github.com/davila7/5b07f55a6e65a06c121da9702d10c2e2

> Claude will read the gist, create the config file, and you're done. If you prefer to do it manually:

Claude が gist を読み込み、設定ファイルを作成してくれる。それで完了だ。手動でやりたい場合は：

> How I Manage Panels in Ghostty

Ghostty でのパネル管理方法

> Using Ghostty with Claude Code works best with split panels you might have Claude on one side, git changes on another, maybe a file browser on a third If you can't split, navigate, and close panels without thinking you end up fumbling with shortcuts instead of coding.

Ghostty と Claude Code の組み合わせは、画面を分割したパネルで使うのが最適だ。片側に Claude、もう片側に git の変更、さらに3つ目にファイルブラウザを置くといった具合だ。パネルを分割・移動・閉じる操作を無意識にできなければ、コーディングの代わりにショートカットをもたつくことになる。

> I kept forgetting Ghostty's keybindings so I organized them into a mnemonic SAND Four letters, four actions every panel operation falls into one of these categories

Ghostty のキーバインドをよく忘れてしまうので、SAND というニーモニックに整理した。4文字、4つのアクション。すべてのパネル操作はこのカテゴリのどれかに当てはまる。

> S - Split: Create new panels

S - Split（分割）：新しいパネルを作成する

> Split your terminal into multiple panels.
>
> Cmd+D splits right (vertical)
>
> Cmd+Shift+D splits down (horizontal)

ターミナルを複数のパネルに分割する。
- Cmd+D：右に分割（縦）
- Cmd+Shift+D：下に分割（横）

> A - Across: Move between tabs

A - Across（横断）：タブ間を移動する

> Navigate across tabs.
>
> Cmd+T opens a new tab
>
> Cmd+Shift+Left/Right moves between them

タブ間を移動する。
- Cmd+T：新しいタブを開く
- Cmd+Shift+Left/Right：タブ間を移動する

> N - Navigate: Jump between split panels

N - Navigate（ナビゲート）：分割パネル間をジャンプする

> Move focus between your splits.
>
> Cmd+Alt+Arrows jumps in any direction
>
> Cmd+Shift+E equalizes all splits
>
> Cmd+Shift+F zooms into one panel (press again to restore)

分割パネル間でフォーカスを移動する。
- Cmd+Alt+Arrows：任意の方向にジャンプ
- Cmd+Shift+E：全分割を均等化
- Cmd+Shift+F：1つのパネルにズームイン（再度押すと元に戻る）

> D - Destroy: Close panels and tabs

D - Destroy（破棄）：パネルとタブを閉じる

> Close what you don't need. Cmd+W closes the current panel or tab.

不要なものを閉じる。Cmd+W で現在のパネルまたはタブを閉じる。

> My Workflow Layout

私のワークフローレイアウト

> This is what my daily setup looks like, and it scales from 1 to 3 Claude Code instances running in parallel... remember use SAND!

これが私の日常的なセットアップで、Claude Code のインスタンスを1〜3個並列で動かすことができる……SAND を使うことを忘れずに！

> Start simple: one Claude Code panel on the left, S (Cmd+D) to split right, and run lazygit there to monitor every commit and diff Claude makes in real time.

シンプルに始める：左に Claude Code パネルを1つ、S（Cmd+D）で右に分割し、そこで lazygit を実行して Claude が行うすべてのコミットと差分をリアルタイムで監視する。

> Then S again (Cmd+Shift+D) to split the right panel down and open yazi as a file browser:

さらに S（Cmd+Shift+D）で右パネルを下に分割し、ファイルブラウザとして yazi を開く：

> But when you're working on multiple tasks, you can split the left side into 2 or 3 Claude Code instances, each running on a different Git worktree:

複数のタスクに取り組む場合は、左側を2〜3つの Claude Code インスタンスに分割し、それぞれ異なる Git ワークツリーで実行できる：

> If some Claude Code panels get too big because you need more context you can press Cmd+Shift+E to equalize all windows and bring them back to a balanced layout

コンテキストが必要で一部の Claude Code パネルが大きくなりすぎた場合は、Cmd+Shift+E を押してすべてのウィンドウを均等化し、バランスの取れたレイアウトに戻せる。

> That's the power of combining Ghostty with worktrees you go from a single agent to a multi-agent setup without leaving your terminal

これが Ghostty とワークツリーを組み合わせる力だ。ターミナルを離れることなく、シングルエージェントからマルチエージェントのセットアップに移行できる。

> Tip:
>
> stick a post-it with the letters SAND somewhere you can see it every time you see it, practice the commands after a week you'll have Ghostty fully under control from the keyboard

ヒント：
SAND の文字を書いたポストイットを見える場所に貼っておこう。見るたびにコマンドを練習すれば、1週間後にはキーボードから Ghostty を完全にコントロールできるようになる。

> Next Articles

次の記事

> This was the first article ehe next two will show how I work with Ghostty and Claude Code

これが第1弾の記事だ。次の2本では Ghostty と Claude Code を使った作業方法を紹介する。

> One article will cover Lazygit, watch Claude Code's commits, diffs, and branch changes in real time

1本は Lazygit を取り上げ、Claude Code のコミット、差分、ブランチの変更をリアルタイムで監視する方法を紹介する。

> The other will cover git worktrees and parallel agents, run multiple Claude Code instances on different tasks and use yazi to browse project files

もう1本は git ワークツリーと並列エージェントを取り上げ、複数の Claude Code インスタンスを異なるタスクで実行し、yazi を使ってプロジェクトファイルを閲覧する方法を紹介する。

> Follow me to catch the next articles! 👇

次の記事をお見逃しなく！フォローしてください！ 👇
