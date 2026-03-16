---
name: delegation-boundaries
description: Explains what can be delegated to sub-agents, to whom, under what evidence requirements, and when escalation is required. Trigger when designing multi-agent task distribution. Do NOT use for single-agent execution decisions.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agentic-orchestration-and-autonomy
  priority: P0
  maturity: draft
  risk: low
  tags: [delegation, boundaries, escalation]
---

# Purpose
Defines the rules for what work can be delegated to sub-agents, what evidence must be present, and when escalation back to the orchestrator is required.

# When to use this skill
Use when:
- Designing a multi-agent system and deciding which agents can work autonomously
- A task boundary is unclear between a manager agent and an implementer agent

Do NOT use when:
- Working within a single agent context with no sub-delegation
- The full task is already scoped to one agent role

# Operating procedure
1. Enumerate all sub-agent roles and their permitted actions
2. For each action, specify the required evidence and preconditions
3. Define escalation triggers (e.g., ambiguity, blocked state, out-of-scope request)
4. Document what is never delegatable (e.g., destructive irreversible operations)

# Output defaults
A delegation boundary table listing roles, permitted actions, required evidence, and escalation conditions.

# Failure handling
If an agent attempts an action outside its delegation boundary, halt the action, escalate to the orchestrator, and log the boundary violation.
