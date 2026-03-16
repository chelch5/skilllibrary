---
name: vllm-serving
description: Handles vLLM-based serving, batching, throughput optimisation, and API integration where GPU infrastructure justifies it. Use when deploying high-throughput GPU inference with vLLM. Do NOT use for CPU-only setups.
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
  tags: [vllm, gpu, serving, throughput, batching]
---

# Purpose
Configures and operates vLLM for high-throughput GPU inference with continuous batching, OpenAI-compatible API, and operational monitoring.

# When to use this skill
Use when:
- Deploying a model with vLLM for production or high-load scenarios
- Tuning continuous batching, max-model-len, and tensor parallelism
- Exposing an OpenAI-compatible inference endpoint

Do NOT use when:
- CPU-only inference (use offline-cpu-inference or llama-cpp)
- Development/local use (use ollama)

# Operating procedure
1. Install vLLM with CUDA support: pip install vllm
2. Launch: python -m vllm.entrypoints.openai.api_server --model modelname
3. Set --max-model-len to fit within VRAM; reduce if OOM
4. Set --tensor-parallel-size for multi-GPU setups
5. Set --max-num-seqs for concurrent request limit
6. Add --api-key for basic auth; front with nginx for TLS

# Output defaults
vLLM launch command + Docker/systemd wrapper + VRAM sizing guide + client example.

# Failure handling
On CUDA OOM, reduce --max-model-len or use --quantization awq. On request timeout, reduce --max-num-seqs. Monitor GPU utilisation with nvidia-smi.
