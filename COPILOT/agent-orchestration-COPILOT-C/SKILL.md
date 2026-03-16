---
name: agent-orchestration
description: Coordinates multiple agents, defines responsibility boundaries, and sequences collaborative work safely. Trigger when a task requires multiple specialized agents to work together in a defined sequence. Do NOT use for single-agent tasks or simple tool calls.
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
  tags: [orchestration, multi-agent, coordination]
---

# Purpose
Coordinates multiple agents by defining responsibility boundaries and sequencing collaborative work safely across agent roles.

# When to use this skill
Use when:
- A task requires multiple specialized agents working together
- Coordination between planning, implementation, and review agents is needed

Do NOT use when:
- Only one agent is needed for the task
- The task is simple enough for direct tool calls without orchestration

# Operating procedure
1. Identify the agents required and their responsibilities
2. Define handoff artifacts and acceptance criteria between agents
3. Sequence work so dependencies are respected and no two agents mutate the same surface simultaneously
4. Monitor outputs and validate before advancing to the next stage

# Output defaults
An orchestration plan document listing agent roles, sequence, handoff artifacts, and escalation conditions.

# Failure handling
If an agent fails to produce a required artifact, pause the chain, surface the failure, and rerun only the failed stage before continuing.
