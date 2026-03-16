---
name: eval-dataset-design
description: Designs held-out evaluation datasets with appropriate difficulty, diversity, and contamination safeguards. Use when creating datasets specifically for evaluating trained models. Do NOT use for training data design.
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
  tags: [eval, dataset, held-out, contamination, diversity]
---

# Purpose
Establishes eval dataset design principles: held-out splits, difficulty stratification, diversity coverage, and contamination prevention.

# When to use this skill
Use when:
- Creating a held-out evaluation set for a fine-tuned or pretrained model
- Ensuring eval data does not overlap with training data
- Designing adversarial or challenging evaluation examples

Do NOT use when:
- Training dataset curation (use dataset-curation)
- Benchmark research methodology (use benchmark-design)

# Operating procedure
1. Source eval examples independently from training data sources
2. Run contamination check: n-gram overlap with training corpus
3. Stratify by difficulty: rule-based, model-based, or human-rated
4. Ensure coverage: domain, length, format, and edge case diversity
5. Lock the eval set before training begins; never update mid-run
6. Document collection methodology and annotator instructions

# Output defaults
Eval dataset schema + contamination check script + diversity audit report.

# Failure handling
On contamination detection, exclude contaminated examples and expand clean sources. On coverage gaps, collect targeted examples for underrepresented categories.
