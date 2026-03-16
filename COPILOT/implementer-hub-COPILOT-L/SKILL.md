---
name: implementer-hub
description: Implements changes in the hub, core, or service layer under an approved plan. Trigger when an approved plan targets the central service or hub layer. Do NOT use for context, node-agent, or frontend changes.
source: github.com/gpttalker/gpttalker-agent
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P2
  maturity: draft
  risk: low
  tags: [implementer, hub, service-layer]
---

# Purpose
Executes bounded implementation changes in the hub or core service layer following an approved plan.

# When to use this skill
Use when:
- An approved plan targets the hub or central service layer
- Changes are scoped to core business logic, routing, or service orchestration

Do NOT use when:
- Changes are in the context, retrieval, or node-agent layer (use the respective implementer)
- No approved plan exists (create a plan first)

# Operating procedure
1. Read and confirm the approved plan before touching any code
2. Implement changes step by step as specified in the plan
3. Run applicable tests after each significant change
4. Produce a completion artifact referencing each plan step and its outcome

# Output defaults
A completion report listing each plan step, the change made, and test results.

# Failure handling
If a step fails or produces unexpected results, stop, document the failure, and escalate to the planner for re-planning.
