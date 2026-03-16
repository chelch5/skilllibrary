---
name: model-architecture
description: Designs transformer and LLM architecture components including attention, FFN, positional encoding, and normalisation. Use when designing or modifying model architecture. Do NOT use for training setup or serving.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-training-architecture-and-research
  priority: P0
  maturity: draft
  risk: low
  tags: [architecture, transformer, attention, llm-design, research]
---

# Purpose
Guides transformer architecture design decisions: model depth vs width, attention mechanism, positional encoding, and normalisation strategy.

# When to use this skill
Use when:
- Designing a new transformer architecture or variant
- Choosing between architectural options (GQA, RoPE, RMSNorm, SwiGLU)
- Ablating architectural components on small-scale experiments

Do NOT use when:
- High-level LLM project planning (use llm-creation)
- MoE-specific architecture (use moe-architecture)

# Operating procedure
1. Start from a reference architecture (Llama, Mistral, Falcon) as a baseline
2. Define model dimensions: d_model, n_heads, n_layers, d_ffn (typically 4×)
3. Choose attention: MHA, MQA, or GQA (GQA recommended for KV cache efficiency)
4. Choose positional encoding: RoPE (preferred for length generalisation)
5. Choose normalisation: RMSNorm (preferred); layer norm position: pre-norm
6. Choose activation: SwiGLU or GeLU; add gating for FFN

# Output defaults
Architecture configuration table + rationale for each component choice + parameter count calculation.

# Failure handling
On instability during training, check normalisation placement and initialisation scale. On poor length generalisation, verify positional encoding implementation.
