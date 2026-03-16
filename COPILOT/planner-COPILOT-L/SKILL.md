---
name: planner
description: Turns a single ticket into a complete, bounded implementation plan rather than re-planning the entire project. Trigger when an implementer needs a concrete plan before starting work. Do NOT use to re-plan the whole project or decompose goals (use goal-decomposition instead).
source: github.com/gpttalker/gpttalker-agent
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P1
  maturity: draft
  risk: low
  tags: [planning, tickets, implementation]
---

# Purpose
Converts a single well-scoped ticket into a concrete, bounded implementation plan with steps, dependencies, and acceptance criteria.

# When to use this skill
Use when:
- An implementer needs a step-by-step plan before touching code
- A ticket is underspecified and needs to be fleshed out before work begins

Do NOT use when:
- The full project backlog needs re-planning (use goal-decomposition)
- The ticket is already fully specified with clear steps

# Operating procedure
1. Read the ticket description and acceptance criteria
2. Identify the smallest scope of change that satisfies the ticket
3. Break the work into ordered implementation steps with file/module targets
4. Note dependencies and potential conflicts
5. Produce a plan artifact that the implementer can execute step by step

# Output defaults
A plan document with: ticket reference, scope summary, ordered steps, file targets, and acceptance criteria checklist.

# Failure handling
If the ticket is too ambiguous to plan, return a clarification request listing the specific gaps before proceeding.
