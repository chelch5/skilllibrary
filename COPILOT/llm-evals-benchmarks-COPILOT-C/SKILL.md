---
name: llm-evals-benchmarks
description: Creates task-specific evaluations for model quality, latency, reliability, and regressions. Use when setting up LLM evaluation pipelines. Do NOT use for training-time benchmarks.
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
  tags: [evals, benchmarks, quality, regression, llm]
---

# Purpose
Establishes task-specific eval harnesses that measure model quality, catch regressions, and track latency across model updates.

# When to use this skill
Use when:
- Setting up automated evals before shipping a model change
- Designing prompt regression tests
- Comparing two model versions on a task-specific dataset

Do NOT use when:
- Research-scale pretraining benchmarks (use benchmark-design in cat-12)
- Training-time loss monitoring

# Operating procedure
1. Define task-specific golden dataset (inputs + expected outputs)
2. Choose metrics: exact match, F1, ROUGE, LLM-as-judge, or custom
3. Run eval harness (LangSmith, promptfoo, Eleuther lm-eval, or custom)
4. Set pass/fail thresholds for CI integration
5. Track metric history to detect gradual regression
6. Review failing cases manually before dismissing as noise

# Output defaults
Eval dataset schema + runner script + metric definitions + CI integration step.

# Failure handling
On eval failure above threshold, block deployment and surface failing examples. Never ship a model update that degrades a production task metric without explicit sign-off.
