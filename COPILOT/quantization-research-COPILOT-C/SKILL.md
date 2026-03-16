---
name: quantization-research
description: Researches and experiments with novel quantization algorithms for LLM compression. Use for research into new quantization methods. Do NOT use for production quantization decisions.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-training-architecture-and-research
  priority: P1
  maturity: draft
  risk: low
  tags: [quantization, research, gptq, awq, squeezellm, algorithms]
---

# Purpose
Guides research-oriented quantization experiments: algorithm comparison (GPTQ, AWQ, SqueezeLLM), calibration data design, and quality measurement.

# When to use this skill
Use when:
- Researching a new or improved quantization algorithm
- Comparing post-training quantization (PTQ) vs quantization-aware training (QAT)
- Running calibration experiments to improve low-bit quantization quality

Do NOT use when:
- Selecting quantization for production deployment (use quantization-strategy in cat-11)
- General model compression (use distillation-compression)

# Operating procedure
1. Define target: bit-width, quality floor, hardware target
2. Implement or apply PTQ algorithm with calibration dataset (128–512 samples)
3. Measure perplexity and task accuracy vs FP16 baseline
4. Compare algorithms at same bit-width; report quality-memory tradeoff
5. Test numerical stability across diverse input distributions
6. Document calibration data sensitivity and reproducibility

# Output defaults
Quantization experiment results table + calibration procedure + algorithm comparison.

# Failure handling
On calibration instability, diversify calibration samples. On large quality gap vs FP16, investigate outlier channels and apply per-channel scaling.
