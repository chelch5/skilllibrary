---
name: manager-hierarchy-design
description: Decides when to introduce managers, section leads, or a second orchestration tier above team leaders. Trigger when a multi-agent system grows complex enough to need a management hierarchy. Do NOT use for simple two-layer agent systems.
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
  tags: [hierarchy, management, orchestration]
---

# Purpose
Provides design guidance for when and how to introduce a management hierarchy above team leaders in complex multi-agent systems.

# When to use this skill
Use when:
- A multi-agent system has grown to the point where team leaders themselves need coordination
- Designing a large-scale autonomous system with multiple specialized teams

Do NOT use when:
- The system has only one or two agent layers
- A flat team structure is sufficient for the workload

# Operating procedure
1. Assess the current agent team structure and identify coordination bottlenecks
2. Determine if a manager tier would reduce bottlenecks or add unnecessary overhead
3. Define manager responsibilities (resource allocation, cross-team conflict resolution, priority setting)
4. Design escalation paths from team leaders to managers to the top-level orchestrator
5. Document the hierarchy and decision authority at each level

# Output defaults
A hierarchy design document with agent tiers, responsibilities, escalation paths, and authority boundaries.

# Failure handling
If the hierarchy design creates more complexity than it solves, recommend staying flat and document the trade-off analysis.
