---
name: dense-to-moe-experiments
description: Guides experiments converting dense transformer checkpoints to Mixture-of-Experts architectures. Use when experimenting with MoE upcycling. Do NOT use for production MoE architecture design.
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
  tags: [moe, dense, upcycling, experiments, architecture]
---

# Purpose
Establishes an experimental framework for converting dense model checkpoints into MoE architectures via expert upcycling or branch-and-continue training.

# When to use this skill
Use when:
- Experimenting with MoE upcycling from a dense checkpoint
- Comparing dense vs sparse models at equivalent activated parameter counts
- Designing ablations for expert granularity and routing strategy

Do NOT use when:
- Designing a production MoE model from scratch (use moe-architecture)
- Training a standard dense model (use pretraining-pipeline)

# Operating procedure
1. Start from a converged dense checkpoint as the base
2. Split FFN layers into N experts; initialise each expert from the original weights
3. Add router network; initialise to uniform distribution
4. Continue training with MoE-specific learning rate and router auxiliary loss
5. Monitor expert utilisation; target balanced load (entropy > log(N) - 0.5)
6. Compare perplexity and downstream task scores vs dense baseline

# Output defaults
Upcycling script + router initialisation + training config delta + evaluation comparison.

# Failure handling
On expert collapse (one expert dominates), increase auxiliary loss coefficient. On perplexity regression vs dense, verify expert initialisation was correct.
