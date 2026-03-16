---
name: data-cleaning-labeling
description: Establishes procedures for cleaning raw text data and producing high-quality labels for LLM training. Use when preparing training data. Do NOT use for inference-time data processing.
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
  tags: [data-cleaning, labeling, training-data, quality, annotation]
---

# Purpose
Provides systematic data cleaning and labeling procedures that produce consistent, high-quality training data with auditable decisions.

# When to use this skill
Use when:
- Cleaning raw web or document data for LLM training
- Setting up a labeling workflow with inter-annotator agreement
- Designing data quality filters and deduplication

Do NOT use when:
- Inference-time input validation (use api-contracts or fastapi)
- Benchmark dataset creation (use benchmark-design)

# Operating procedure
1. Profile raw data: length distribution, language detection, encoding issues
2. Apply quality filters: length, perplexity, n-gram dedup (MinHash LSH)
3. Remove PII with NER-based scrubbing; flag uncertain cases for review
4. Define labeling schema with explicit guidelines and edge case examples
5. Measure inter-annotator agreement (Cohen's kappa); retrain if below 0.7
6. Version the cleaned dataset with a hash for reproducibility

# Output defaults
Cleaning pipeline script + labeling schema + IAA measurement + dataset version manifest.

# Failure handling
On low inter-annotator agreement, hold disputed examples for adjudication. On PII scrubbing uncertainty, exclude the document rather than partially scrub.
