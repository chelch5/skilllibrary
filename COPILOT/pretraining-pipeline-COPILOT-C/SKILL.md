---
name: pretraining-pipeline
description: Sets up and operates LLM pretraining pipelines covering data loading, distributed training, checkpointing, and stability monitoring. Use when running a pretraining run. Do NOT use for fine-tuning.
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
  tags: [pretraining, distributed, checkpointing, stability, data-loading]
---

# Purpose
Establishes a production-grade pretraining pipeline with distributed training, checkpoint management, and loss monitoring for LLM training runs.

# When to use this skill
Use when:
- Setting up a new pretraining run on a GPU cluster
- Designing checkpoint strategy and resume-from-checkpoint logic
- Monitoring training stability (loss curves, gradient norms)

Do NOT use when:
- Fine-tuning an existing model (use fine-tuning)
- Infrastructure provisioning (use training-infrastructure)

# Operating procedure
1. Configure distributed training: FSDP or Megatron-LM for large runs
2. Set up data pipeline with streaming and shuffled data loading
3. Configure checkpointing: save every N steps with async upload to object storage
4. Monitor: loss curve, gradient norm, learning rate, GPU utilisation
5. Set loss spike detection: alert if loss increases >10% over 100 steps
6. Define restart procedure: rollback to last stable checkpoint on divergence

# Output defaults
Training launch script + checkpoint config + monitoring dashboard setup + rollback procedure.

# Failure handling
On loss divergence, roll back to the last stable checkpoint and reduce learning rate by 2×. On hardware failure, resume from last checkpoint with NCCL timeout tuning.
