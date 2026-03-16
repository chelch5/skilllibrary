---
name: dataset-curation
description: Curates high-quality datasets for LLM training by selecting, mixing, and weighting data sources. Use when assembling a training corpus. Do NOT use for inference data preparation.
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
  tags: [dataset, curation, data-mix, training, corpus]
---

# Purpose
Guides selection, mixing, and quality-weighted combination of data sources to produce a training corpus aligned with model objectives.

# When to use this skill
Use when:
- Selecting and mixing data sources for pretraining or fine-tuning
- Designing domain-specific data weighting strategies
- Auditing dataset composition for bias or harmful content

Do NOT use when:
- Cleaning or labeling individual documents (use data-cleaning-labeling)
- Synthetic data generation (use synthetic-data-generation)

# Operating procedure
1. Define target capabilities and map to data source types
2. Inventory candidate sources: licence, recency, domain coverage
3. Sample and manually review 100 random examples per source
4. Set domain mixing weights; up-weight high-quality sources
5. Apply global quality filter (perplexity, dedup) across the full mix
6. Document final mix ratios and total token counts

# Output defaults
Dataset manifest with source weights + quality filter config + token count summary.

# Failure handling
On licence ambiguity, exclude the source. On quality filter removing >30% of a source, investigate filtering thresholds before proceeding.
