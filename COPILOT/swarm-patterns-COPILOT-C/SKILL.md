---
name: swarm-patterns
description: Defines reusable collaboration patterns for many agents working on one outcome with bounded overlap. Trigger when designing a society-of-agents or swarm-style execution model. Do NOT use for small two or three agent systems where simple delegation suffices.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P2
  maturity: draft
  risk: low
  tags: [swarm, patterns, multi-agent]
---

# Purpose
Catalogs reusable swarm collaboration patterns that enable many agents to work toward a shared outcome while minimizing destructive overlap.

# When to use this skill
Use when:
- Designing a large-scale multi-agent system with many parallel workers
- Choosing between scatter-gather, pipeline, consensus, or auction swarm patterns

Do NOT use when:
- Only two or three agents are involved (simple delegation is sufficient)
- Sequential pipeline is already the correct model

# Operating procedure
1. Identify the nature of the work: can it be partitioned, pipelined, or does it require consensus?
2. Select an appropriate swarm pattern (scatter-gather, pipeline, voting, market/auction)
3. Define how agents enter and exit the swarm, what they produce, and how results are merged
4. Define conflict resolution: who arbitrates when two agents produce incompatible results?
5. Document the chosen pattern with a reference implementation

# Output defaults
A swarm design document with pattern name, agent roles, work distribution strategy, merge protocol, and conflict resolution.

# Failure handling
If agents produce irreconcilable outputs, escalate to the team leader for arbitration rather than silently choosing one result.
