---
saved_at: "2026-02-20T06:16:16.056Z"
source_url: "https://huggingface.co/sweepai/sweep-next-edit-1.5B"
source_app: "ios-share-extension"
page_title: "sweepai/sweep-next-edit-1.5B · Hugging Face"
note: ""
content_type: "text/html; charset=utf-8"
extractor: "html-readability"
---

# sweepai/sweep-next-edit-1.5B · Hugging Face

A 1.5B parameter model for next-edit autocomplete, quantized to Q8\_0 GGUF format.

## [](#model-description)Model Description

Sweep Next-Edit predicts your next code edit before you make it. It runs locally on your laptop in under 500ms (with speculative decoding) and outperforms models over 4x its size on next-edit benchmarks. More details [here](https://blog.sweep.dev/posts/oss-next-edit).

## [](#usage)Usage

Download `run_model.py` and the model file, then:

```
uv pip install llama-cpp-python huggingface_hub
python run_model.py
```

## [](#model-details)Model Details

-   **Format**: GGUF (Q8\_0 quantization)
-   **Parameters**: 1.5B
-   **Context Length**: 8192 tokens
-   **Base Model**: Qwen2.5-Coder

## [](#example)Example

The model uses a specific prompt format with file context, recent diffs, and current state to predict the next edit. See `run_model.py` for a complete example.

## [](#links)Links

-   [Blog Post](https://blog.sweep.dev/posts/oss-next-edit) - Technical details and benchmarks
-   [JetBrains Plugin](https://plugins.jetbrains.com/plugin/26860-sweep-ai-autocomplete--coding-agent) - Sweep AI JetBrains Plugin
-   [HN Thread](https://news.ycombinator.com/item?id=46713106) - Discuss implementation for VSCode, Neovim & Emacs
-   [Twitter Post](https://x.com/sweepai/status/2014045512417345883) - Ask us any other questions

## [](#license)License

Apache 2.0
