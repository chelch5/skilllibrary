---
name: model-merging
description: Combines weights from multiple fine-tuned models via merging techniques (SLERP, TIES, DARE). Use when combining specialised models without retraining. Do NOT use for standard model training.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-training-architecture-and-research
  priority: P2
  maturity: draft
  risk: low
  tags: [model-merging, slerp, ties, dare, weight-averaging]
---

# Purpose
Applies model merging techniques to combine multiple fine-tuned checkpoints into a single model with blended capabilities.

# When to use this skill
Use when:
- Combining a coding model and a reasoning model without retraining
- Experimenting with SLERP, TIES, or DARE merging methods
- Evaluating merged model quality vs individual checkpoints

Do NOT use when:
- Training a new model from scratch
- Distillation (use distillation-compression)

# Operating procedure
1. Select base model and candidate checkpoints to merge (must share architecture)
2. Choose merge method: SLERP (two models), TIES (multi-model, sign conflict resolution), DARE (sparse delta)
3. Set merge coefficients; start with equal weights
4. Run merge with mergekit or custom script
5. Evaluate merged model on tasks from each source model
6. Iterate coefficients to optimise task balance

# Output defaults
Merge config (mergekit YAML) + evaluation results per task + recommended coefficients.

# Failure handling
On degraded performance vs either source model, try lower merge coefficients or switch to TIES with higher pruning ratio. On architecture mismatch error, verify all checkpoints are the same base model.
