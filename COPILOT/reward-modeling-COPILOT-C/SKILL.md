---
name: reward-modeling
description: Trains reward models for RLHF pipelines from human preference data. Use when building a reward model for preference optimisation. Do NOT use for final policy training.
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
  tags: [reward-model, rlhf, preferences, bradley-terry, rm-training]
---

# Purpose
Establishes reward model training from preference pairs, including architecture choices, training procedure, and validation of reward signal quality.

# When to use this skill
Use when:
- Training a reward model from human preference annotations
- Validating reward model agreement with human judgment
- Designing the reward model architecture relative to the policy model

Do NOT use when:
- Direct preference optimisation without a separate RM (use preference-optimization with DPO)
- General fine-tuning (use fine-tuning)

# Operating procedure
1. Format data as (prompt, chosen, rejected) preference pairs
2. Use base model of same or slightly smaller scale as reward backbone
3. Replace language model head with a scalar reward head
4. Train with Bradley-Terry pairwise ranking loss
5. Validate: reward model should prefer chosen over rejected on held-out set (>70% accuracy)
6. Test for reward hacking signal: evaluate on adversarial inputs before using in RLHF

# Output defaults
Reward model architecture config + training script + validation accuracy measurement.

# Failure handling
On reward model accuracy below 65%, collect more preference data and check labeling quality. On reward hacking in downstream RLHF, add reward normalisation and KL penalty.
