---
name: llama-cpp
description: Applies llama.cpp runtime patterns, quantization considerations, and local deployment habits. Use when running models with llama.cpp or llama-cpp-python. Do NOT use for GPU-only serving stacks.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-runtime-and-integration
  priority: P1
  maturity: draft
  risk: low
  tags: [llama-cpp, local, quantization, gguf, cpu]
---

# Purpose
Provides practical llama.cpp setup and usage patterns: GGUF model selection, quantization level choice, context window management, and Python binding usage.

# When to use this skill
Use when:
- Running local models via llama.cpp or llama-cpp-python
- Choosing between Q4_K_M, Q5_K_M, Q8_0 quantization
- Configuring n_ctx, n_threads, and n_gpu_layers for a given machine

Do NOT use when:
- vLLM or TGI GPU serving (use vllm-serving or inference-serving)
- Ollama-managed model lifecycle (use ollama)

# Operating procedure
1. Download GGUF model from HuggingFace; verify SHA256
2. Choose quantization: Q4_K_M for balance, Q8_0 for quality, Q2_K for minimum RAM
3. Set n_threads to physical CPU core count; n_gpu_layers=0 for pure CPU
4. Set n_ctx to task requirement; higher = more RAM
5. Use llama-cpp-python with Llama() for Python integration
6. Benchmark tokens/s at chosen settings before committing

# Output defaults
Model download command + Llama() initialisation + quantization selection guide.

# Failure handling
On OOM, reduce n_ctx or switch to a lower quantization tier. On slow inference, increase n_threads and verify no GPU layers are silently falling back to CPU.
