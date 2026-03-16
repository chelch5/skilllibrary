---
name: goal-decomposition
description: Breaks broad goals into staged work units, subgoals, dependencies, and decision checkpoints. Trigger when a high-level objective needs to be converted into an actionable plan. Do NOT use when the task is already granular and ready to execute.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agentic-orchestration-and-autonomy
  priority: P1
  maturity: draft
  risk: low
  tags: [decomposition, planning, goals]
---

# Purpose
Transforms broad, ambiguous goals into concrete, ordered work units with explicit dependencies and decision checkpoints.

# When to use this skill
Use when:
- A goal is too large or vague to act on directly
- A plan needs to be created before an autonomous run begins

Do NOT use when:
- The task is already fully specified as tickets or steps
- The goal is trivially small (one or two actions)

# Operating procedure
1. State the top-level goal clearly
2. Identify major subgoals and their dependencies
3. Break each subgoal into concrete work units with acceptance criteria
4. Mark decision checkpoints where new information might redirect the plan
5. Order the work units by dependency and risk

# Output defaults
A structured goal decomposition tree with subgoals, work units, dependencies, and checkpoints in Markdown or ticket format.

# Failure handling
If a subgoal cannot be decomposed due to missing information, flag it as a research gap and generate a research task before proceeding.
