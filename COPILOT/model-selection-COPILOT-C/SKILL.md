---
name: model-selection
description: Chooses a model based on task shape, hardware, latency, cost, context, and risk tolerance. Use at the start of a new AI feature. Do NOT use for ongoing routing decisions.
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
  tags: [model-selection, evaluation, tradeoffs, capability, cost]
---

# Purpose
Provides a structured decision framework for choosing the right model for a task considering capability, cost, latency, and operational constraints.

# When to use this skill
Use when:
- Starting a new AI feature and selecting an initial model
- Comparing two candidate models for a specific task
- Re-evaluating model choice after cost or performance changes

Do NOT use when:
- Runtime request-level routing (use model-routing)
- Model fine-tuning decisions (use fine-tuning in cat-12)

# Operating procedure
1. Define task requirements: input/output modality, context length, latency SLA, cost budget
2. List candidate models; filter by hard constraints (context, modality, availability)
3. Run task-specific evaluation on a golden set (10–50 examples)
4. Score on quality, latency p50/p99, and cost per 1K tokens
5. Select best-fit; document decision rationale and tradeoffs
6. Set review trigger: re-evaluate on price changes or model releases

# Output defaults
Selection matrix (model vs criteria) + eval results summary + rationale document.

# Failure handling
If no model meets all criteria, identify the most relaxable constraint and document the tradeoff. Never select a model without task-specific testing.
