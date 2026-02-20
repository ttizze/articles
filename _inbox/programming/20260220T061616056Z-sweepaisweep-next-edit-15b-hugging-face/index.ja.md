---
saved_at: "2026-02-20T06:16:16.056Z"
source_url: "https://huggingface.co/sweepai/sweep-next-edit-1.5B"
source_app: "ios-share-extension"
page_title: "sweepai/sweep-next-edit-1.5B · Hugging Face"
note: ""
content_type: "text/html; charset=utf-8"
extractor: "html-readability"
---

> # sweepai/sweep-next-edit-1.5B · Hugging Face

# sweepai/sweep-next-edit-1.5B · Hugging Face

> A 1.5B parameter model for next-edit autocomplete, quantized to Q8\_0 GGUF format.

Q8\_0 GGUF形式に量子化された、次の編集自動補完のための15億パラメータモデルです。

> ## [](#model-description)Model Description

## モデルの説明

> Sweep Next-Edit predicts your next code edit before you make it. It runs locally on your laptop in under 500ms (with speculative decoding) and outperforms models over 4x its size on next-edit benchmarks. More details [here](https://blog.sweep.dev/posts/oss-next-edit).

Sweep Next-Editは、次のコード編集を行う前にそれを予測します。投機的デコードを用いてラップトップ上でローカルに500ms未満で動作し、次の編集ベンチマークでは自身の4倍以上のサイズのモデルを上回ります。詳細は[こちら](https://blog.sweep.dev/posts/oss-next-edit)をご覧ください。

> ## [](#usage)Usage

## 使用方法

> Download `run_model.py` and the model file, then:

`run_model.py` とモデルファイルをダウンロードして、以下を実行してください:

> ```
> uv pip install llama-cpp-python huggingface_hub
> python run_model.py
> ```

> ## [](#model-details)Model Details

## モデルの詳細

> -   **Format**: GGUF (Q8\_0 quantization)
> -   **Parameters**: 1.5B
> -   **Context Length**: 8192 tokens
> -   **Base Model**: Qwen2.5-Coder

- **フォーマット**: GGUF（Q8\_0量子化）
- **パラメータ数**: 15億
- **コンテキスト長**: 8192トークン
- **ベースモデル**: Qwen2.5-Coder

> ## [](#example)Example

## 例

> The model uses a specific prompt format with file context, recent diffs, and current state to predict the next edit. See `run_model.py` for a complete example.

このモデルは、ファイルのコンテキスト、最近の差分、現在の状態を含む特定のプロンプト形式を使用して次の編集を予測します。完全な例については `run_model.py` を参照してください。

> ## [](#links)Links

## リンク

> -   [Blog Post](https://blog.sweep.dev/posts/oss-next-edit) - Technical details and benchmarks
> -   [JetBrains Plugin](https://plugins.jetbrains.com/plugin/26860-sweep-ai-autocomplete--coding-agent) - Sweep AI JetBrains Plugin
> -   [HN Thread](https://news.ycombinator.com/item?id=46713106) - Discuss implementation for VSCode, Neovim & Emacs
> -   [Twitter Post](https://x.com/sweepai/status/2014045512417345883) - Ask us any other questions

- [ブログ記事](https://blog.sweep.dev/posts/oss-next-edit) - 技術的詳細とベンチマーク
- [JetBrainsプラグイン](https://plugins.jetbrains.com/plugin/26860-sweep-ai-autocomplete--coding-agent) - Sweep AI JetBrainsプラグイン
- [HNスレッド](https://news.ycombinator.com/item?id=46713106) - VSCode、Neovim、Emacsの実装についての議論
- [Twitterの投稿](https://x.com/sweepai/status/2014045512417345883) - その他のご質問はこちら

> ## [](#license)License

## ライセンス

> Apache 2.0

Apache 2.0
