---
name: implementer-node-agent
description: Implements bounded changes in node-agent or per-machine execution surfaces under an approved plan. Trigger when changes target node-agent execution or per-machine surfaces. Do NOT use for hub/core or context layer changes.
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
  tags: [implementer, node-agent, execution]
---

# Purpose
Executes bounded implementation changes in node-agent or per-machine execution surfaces following an approved plan.

# When to use this skill
Use when:
- An approved plan targets node-agent execution, per-machine logic, or distributed agent surfaces
- Changes affect how individual agents execute tasks on specific nodes

Do NOT use when:
- Changes target the hub/core service layer (use implementer-hub)
- Changes affect context or retrieval systems (use implementer-context)

# Operating procedure
1. Confirm the approved plan and identify affected node-agent components
2. Implement changes step by step, respecting node-specific isolation boundaries
3. Test changes in the node-agent surface and verify no cross-node contamination
4. Produce a completion artifact referencing each step

# Output defaults
A completion report with each plan step, change made, and node-isolation validation.

# Failure handling
If node isolation is breached or unexpected cross-node effects appear, halt and escalate to the planner.
