---
name: implementer-context
description: Implements context, retrieval, routing, or observability changes under an approved plan. Trigger when changes target context management, retrieval pipelines, or observability. Do NOT use for hub/core or node-agent changes.
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
  tags: [implementer, context, retrieval]
---

# Purpose
Executes bounded implementation changes in the context, retrieval, routing, or observability layer following an approved plan.

# When to use this skill
Use when:
- An approved plan targets context management, vector retrieval, routing logic, or observability
- Changes are scoped to information flow and retrieval infrastructure

Do NOT use when:
- Changes are in the hub/core layer (use implementer-hub)
- Changes affect node-agent execution surfaces (use implementer-node-agent)

# Operating procedure
1. Confirm the approved plan and identify affected context/retrieval components
2. Implement changes step by step as specified
3. Validate that retrieval behavior and routing are correct after changes
4. Produce a completion artifact

# Output defaults
A completion report with each plan step, change made, and retrieval/routing validation results.

# Failure handling
If retrieval or routing behavior changes unexpectedly, halt, document the regression, and escalate to the planner.
