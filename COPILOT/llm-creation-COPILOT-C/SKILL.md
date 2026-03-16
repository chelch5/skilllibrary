---
name: llm-creation
description: Guides end-to-end creation of a new LLM from architecture design through pretraining to instruction tuning. Use when building a new LLM. Do NOT use for adapting existing models.
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
  tags: [llm-creation, pretraining, architecture, end-to-end, research]
---

# Purpose
Coordinates the full LLM creation lifecycle: architecture decisions, data pipeline, pretraining, instruction tuning, evaluation, and release.

# When to use this skill
Use when:
- Planning a new LLM research or production training run from scratch
- Coordinating across architecture, data, training, and eval sub-teams
- Making high-level tradeoff decisions (scale, data mix, alignment method)

Do NOT use when:
- Adapting or fine-tuning an existing model (use fine-tuning)
- Focused sub-tasks like tokenizer design or architecture (use those skills)

# Operating procedure
1. Define target capabilities, scale, and hardware budget
2. Design architecture (use model-architecture skill)
3. Curate and prepare training data (use dataset-curation + data-cleaning-labeling)
4. Design tokenizer (use tokenizer-design)
5. Set up training infrastructure (use training-infrastructure)
6. Run pretraining (use pretraining-pipeline), then instruction-tuning, then alignment

# Output defaults
LLM project plan + decision log + handoff checklist between pipeline stages.

# Failure handling
At each stage gate, run a quality check before proceeding. On unexpected training divergence, checkpoint rollback to the last stable state.
