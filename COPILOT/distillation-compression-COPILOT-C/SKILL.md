---
name: distillation-compression
description: Guides knowledge distillation and model compression to produce smaller, faster models from larger teachers. Use when reducing model size for deployment. Do NOT use for quantization-only compression.
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
  tags: [distillation, compression, knowledge-transfer, pruning, student-teacher]
---

# Purpose
Provides distillation and compression procedures to create smaller student models that retain teacher model quality on target tasks.

# When to use this skill
Use when:
- Distilling a large model into a smaller, deployable student
- Combining distillation with fine-tuning for domain adaptation
- Evaluating quality-compression tradeoff across student sizes

Do NOT use when:
- Quantization-only compression (use quantization-strategy or quantization-research)
- Training a new model from scratch (use pretraining-pipeline)

# Operating procedure
1. Define target student architecture and size budget
2. Generate teacher logits on a distillation dataset
3. Train student on KL-divergence loss from teacher logits + task loss
4. Tune temperature parameter: higher T for soft label smoothing
5. Evaluate student vs teacher on held-out task benchmarks
6. Optionally apply structured pruning after distillation for further compression

# Output defaults
Distillation training config + loss function implementation + evaluation comparison table.

# Failure handling
On student underperforming target quality, increase teacher dataset size or try a larger intermediate student checkpoint. On training instability, reduce learning rate and increase warmup steps.
