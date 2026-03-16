---
name: python-llm-ml-workflow
description: A broader seed for Python-centric LLM and ML repository work covering project structure, dependency management, and experiment tracking. Use for Python ML project setup. Do NOT use for production serving.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-runtime-and-integration
  priority: P2
  maturity: draft
  risk: low
  tags: [python, ml, llm, workflow, experiment-tracking]
---

# Purpose
Establishes Python ML project conventions: virtual environment management, dependency pinning, experiment tracking, and reproducible runs.

# When to use this skill
Use when:
- Starting a Python LLM or ML project
- Setting up experiment tracking (MLflow, W&B, or simple CSV logs)
- Reviewing Python ML code for reproducibility and dependency hygiene

Do NOT use when:
- Production model serving (use inference-serving or vllm-serving)
- Non-Python projects

# Operating procedure
1. Use uv or poetry for dependency management; pin all versions
2. Create .env for secrets; never commit to version control
3. Use src/ layout with a clear separation of data, models, scripts
4. Track experiments with MLflow or W&B; log hyperparameters and metrics
5. Set random seeds at run start for reproducibility
6. Use hydra or simple argparse for config management

# Output defaults
pyproject.toml template + experiment tracking setup + reproducible run script.

# Failure handling
On dependency conflict, use a fresh virtual environment and re-resolve. On reproducibility failure, verify seed setting and data ordering are deterministic.
