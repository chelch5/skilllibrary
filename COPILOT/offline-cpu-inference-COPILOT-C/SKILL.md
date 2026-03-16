---
name: offline-cpu-inference
description: Optimises and constrains local CPU-only inference setups for machines without GPU. Use when GPU is unavailable or power-constrained. Do NOT use when GPU acceleration is available.
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
  tags: [cpu, offline, inference, quantization, low-resource]
---

# Purpose
Maximises inference quality per watt on CPU-only hardware by selecting appropriate model sizes, quantizations, and runtime settings.

# When to use this skill
Use when:
- Running inference on a machine with no GPU (server, laptop, edge device)
- Selecting the largest model that fits within RAM for CPU inference
- Tuning llama.cpp or similar for CPU-specific throughput

Do NOT use when:
- GPU is available and should be used (use vllm-serving or inference-serving)
- Cloud API inference (use llm-integration)

# Operating procedure
1. Measure available RAM; budget ~1.1× model file size for working memory
2. Choose 3B–7B parameter models for interactive latency on CPU
3. Use Q4_K_M quantization as baseline; Q2_K if RAM is very tight
4. Set n_threads to physical core count (not hyperthreaded)
5. Use mmap to load model; avoids loading entire file into RAM upfront
6. Test tokens/s; target >5 tok/s for usable interactive experience

# Output defaults
RAM sizing guide + quantization selection table + llama.cpp thread config.

# Failure handling
On insufficient RAM to load model, switch to a smaller model before reducing quantization further. On token rate below threshold, document hardware limitation and suggest upgrade path.
