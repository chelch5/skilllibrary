---
name: synthetic-data-generation
description: Generates synthetic training data using LLMs to augment or replace human-labelled datasets. Use when human annotation is scarce or expensive. Do NOT use as a replacement for real-world data without quality checks.
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
  tags: [synthetic-data, augmentation, llm-generated, self-instruct, data-generation]
---

# Purpose
Establishes synthetic data generation pipelines using LLMs for instruction pairs, preference data, or domain-specific augmentation.

# When to use this skill
Use when:
- Generating instruction-response pairs at scale via Self-Instruct or similar
- Augmenting small human-labelled datasets with synthetic examples
- Creating adversarial or edge-case examples for robustness training

Do NOT use when:
- Ground truth quality is critical and synthetic noise is unacceptable
- Generating data for a task where the generator model has known weaknesses

# Operating procedure
1. Define generation schema: prompt template, output format, quality criteria
2. Seed generation with a small set of high-quality human examples (10–100)
3. Generate at scale; apply deduplication and quality filter
4. Validate with human spot-check (10% random sample)
5. Measure distribution coverage: ensure generated data spans the intended skill space
6. Mix synthetic with human data at a calibrated ratio (e.g., 3:1 synthetic:human)

# Output defaults
Generation prompt template + pipeline script + quality filter + human review sampling procedure.

# Failure handling
On low quality generation (>20% failure rate), improve seed examples or add few-shot examples to the generator prompt. Never use unreviewed synthetic data for safety-critical training.
