---
name: quantization-strategy
description: Chooses quantization levels and tradeoffs based on memory, speed, and quality constraints for inference. Use when deciding how to quantize a model for deployment. Do NOT use for training-time quantization research.
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
  tags: [quantization, gguf, bnb, awq, gptq, memory]
---

# Purpose
Provides a practical decision framework for selecting quantization schemes (GGUF, BnB, AWQ, GPTQ) based on hardware and quality requirements.

# When to use this skill
Use when:
- Deciding quantization level for a model before deployment
- Comparing Q4 vs Q8 vs FP16 for a target use case
- Understanding RAM/VRAM requirements at each quantization tier

Do NOT use when:
- Researching new quantization algorithms (use quantization-research in cat-12)
- Training-time quantization-aware training

# Operating procedure
1. Determine quality floor: run a small benchmark at FP16 as baseline
2. Test Q8_0 first: minimal quality loss, 2× memory reduction from FP16
3. Test Q4_K_M: good balance, ~4× reduction, slight quality drop
4. Test Q2_K only if RAM is severely constrained; expect notable degradation
5. For GPU (VRAM): prefer AWQ or GPTQ for better quality at same bit-width
6. Document chosen quantization, measured quality delta, and RAM usage

# Output defaults
Quantization comparison table + hardware requirement table + chosen config.

# Failure handling
If quality drops unacceptably at target quantization, escalate to next tier or use a smaller model with higher precision.
