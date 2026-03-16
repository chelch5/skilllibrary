---
name: misc-helper
description: A catch-all micro-skill for small utility tasks that don't warrant a dedicated skill. Illustrates how lightweight helper skills can exist alongside deep domain packs.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: external-reference-seeds
  priority: P2
  maturity: draft
  risk: low
  tags: [utility, helper, general-purpose, misc]
---

# Purpose
A catch-all micro-skill for small utility tasks that don't warrant a dedicated skill.

# When to use this skill
Use when:
- Small utility tasks without a dedicated skill available
- One-off helper tasks that are simple and bounded
- Quick transformations or lookups

Do NOT use when:
- Complex domain-specific tasks (use appropriate specialized skill)
- Recurring workflows (create a dedicated skill instead)

# Operating procedure
1. Identify the specific utility task
2. Execute the smallest scope approach
3. Validate output against expectation
4. Document if the task recurs frequently
5. Suggest creating a dedicated skill if pattern repeats

# Output defaults
Task-specific output with minimal scope

# Failure handling
If the task is more complex than expected, escalate to a specialized skill.
