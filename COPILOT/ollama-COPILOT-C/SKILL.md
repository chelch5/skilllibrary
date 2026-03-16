---
name: ollama
description: Applies Ollama-specific conventions for model management, serving, and local integration. Use when using Ollama to manage local models. Do NOT use for llama.cpp direct or vLLM deployments.
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
  tags: [ollama, local, model-management, api, gguf]
---

# Purpose
Provides Ollama setup, model management, Modelfile customisation, and API integration patterns for local LLM work.

# When to use this skill
Use when:
- Installing and managing models with Ollama
- Writing a Modelfile to customise system prompt or parameters
- Integrating Ollama's OpenAI-compatible API into an application

Do NOT use when:
- llama.cpp direct usage without Ollama wrapper (use llama-cpp)
- GPU server inference (use vllm-serving)

# Operating procedure
1. Install Ollama; verify with ollama --version
2. Pull model: ollama pull modelname:tag
3. Create Modelfile for custom system prompt or parameter tuning
4. Build custom model: ollama create mymodel -f Modelfile
5. Integrate via OpenAI-compatible endpoint at http://localhost:11434/v1
6. Use OLLAMA_NUM_PARALLEL env to set concurrent request limit

# Output defaults
Modelfile template + API integration snippet + model pull commands.

# Failure handling
On model pull failure, verify disk space and retry. On slow generation, check OLLAMA_NUM_GPU_LAYERS is set appropriately. On port conflict, set OLLAMA_HOST to a different address.
