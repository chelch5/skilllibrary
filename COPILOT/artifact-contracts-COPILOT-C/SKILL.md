---
name: artifact-contracts
description: Specifies what artifacts each workflow stage must produce and what evidence they must contain. Trigger when designing or auditing a multi-stage workflow. Do NOT use for ad-hoc single-step tasks with no handoff requirements.
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
  tags: [artifacts, contracts, handoff]
---

# Purpose
Defines the required output artifacts for each workflow stage and the evidence standards they must meet before handoff.

# When to use this skill
Use when:
- Designing a multi-stage workflow with agent handoffs
- Auditing whether a completed stage actually produced the required outputs

Do NOT use when:
- The task is a single-step execution with no staged handoff
- No formal artifact standards are needed

# Operating procedure
1. Map each workflow stage to its required output artifact(s)
2. Define content requirements for each artifact (must include X, must reference Y)
3. Define the acceptance check: how an agent or reviewer verifies the artifact is complete
4. Reject stages that produce partial or empty artifacts before advancing

# Output defaults
An artifact contract table listing stage, artifact name, required content, and acceptance criteria.

# Failure handling
If an artifact fails acceptance, flag the stage as incomplete. Do not advance the workflow until the artifact is corrected and re-verified.
