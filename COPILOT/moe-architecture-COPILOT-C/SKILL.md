---
name: moe-architecture
description: Designs Mixture-of-Experts architectures including expert routing, load balancing, and capacity factors. Use when designing a production MoE model. Do NOT use for dense transformer design.
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
  tags: [moe, mixture-of-experts, routing, load-balancing, sparse]
---

# Purpose
Guides Mixture-of-Experts architecture design: expert count, routing mechanism, load balancing loss, and capacity factor selection.

# When to use this skill
Use when:
- Designing a sparse MoE LLM architecture
- Choosing between top-1 and top-2 routing strategies
- Setting capacity factors and auxiliary loss weights for balanced expert utilisation

Do NOT use when:
- Dense transformer design (use model-architecture)
- Converting an existing dense model to MoE (use dense-to-moe-experiments)

# Operating procedure
1. Define total parameters vs activated parameters target (e.g., 47B total, 7B activated)
2. Choose expert count and granularity (coarse-grained 8–16 vs fine-grained 64+)
3. Set routing: top-2 routing with auxiliary load balancing loss (coefficient ~0.01)
4. Set capacity factor: 1.25 for training, 2.0 for inference (handles load imbalance)
5. Distribute experts across devices; ensure expert parallelism plan
6. Monitor expert utilisation histograms during early training

# Output defaults
MoE architecture config + router implementation + load balancing loss + capacity factor rationale.

# Failure handling
On expert collapse, increase auxiliary loss coefficient. On capacity overflow (tokens dropped), increase capacity factor or reduce batch size per expert.
