---
name: benchmark-design
description: Designs benchmarks and evaluation criteria to measure agent capabilities and workflow quality. Trigger when establishing success metrics for agents or workflows. Do NOT use for production performance profiling (use frontend-performance or similar).
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P1
  maturity: draft
  risk: low
  tags: [benchmarks, evaluation, metrics]
---

# Purpose
Designs structured benchmarks and evaluation criteria for measuring agent capabilities, workflow quality, and system improvements over time.

# When to use this skill
Use when:
- Establishing baseline performance metrics for a new agent or workflow
- Comparing different agent implementations or prompt strategies

Do NOT use when:
- Profiling production system performance (use dedicated profiling tools)
- Evaluating code quality (use code-review skill)

# Operating procedure
1. Define the capability or workflow dimension to benchmark
2. Design representative test cases with known expected outputs
3. Define scoring criteria (exact match, partial credit, qualitative rubric)
4. Run benchmarks against a baseline and record results
5. Use results to identify gaps and guide improvement iterations

# Output defaults
A benchmark suite with test cases, scoring criteria, baseline results, and improvement recommendations.

# Failure handling
If benchmark results are inconsistent across runs, investigate non-determinism sources before drawing conclusions.
