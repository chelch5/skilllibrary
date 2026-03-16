---
name: local-llm
description: Covers local model runtime selection, deployment constraints, and practical tradeoffs. Use when running LLMs locally without cloud APIs. Do NOT use for hosted or production serving.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-runtime-and-integration
  priority: P0
  maturity: draft
  risk: low
  tags: [local-llm, offline, gguf, ollama, llama-cpp]
---

# Purpose
Guides selection and setup of local LLM runtimes based on hardware constraints, model size, and use-case requirements.

# When to use this skill
Use when:
- Choosing between Ollama, llama.cpp, LM Studio, or other local runtimes
- Sizing a model to fit available RAM and CPU/GPU
- Setting up local inference for privacy-sensitive or offline use cases

Do NOT use when:
- Cloud API integration (use llm-integration)
- High-throughput server inference (use vllm-serving or inference-serving)

# Operating procedure
1. Inventory hardware: RAM, VRAM, CPU cores, OS
2. Rule out models that exceed available RAM (model size * quant factor)
3. Choose runtime: Ollama (ease), llama.cpp (control), LM Studio (GUI)
4. Select model family based on task: code (Codestral, DeepSeek-Coder), chat (Llama-3, Mistral)
5. Validate with a simple prompt before integrating into application
6. Document hardware requirements in README for reproducibility

# Output defaults
Hardware sizing table + runtime selection recommendation + model download + validation test.

# Failure handling
On insufficient RAM, drop to a smaller model or higher quantization. On slow inference, reduce context length or switch to a CPU-optimised quantization.
