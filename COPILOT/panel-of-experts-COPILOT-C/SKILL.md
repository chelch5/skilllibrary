---
name: panel-of-experts
description: Runs a structured multi-perspective pass over a problem before choosing a course of action. Trigger when a high-stakes decision needs multiple viewpoints. Do NOT use for routine low-risk decisions that do not benefit from deliberation.
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
  tags: [panel, experts, deliberation]
---

# Purpose
Structures a multi-expert deliberation process where several perspectives are gathered and weighed before a decision is finalized.

# When to use this skill
Use when:
- A decision is high-stakes or architecturally significant
- Multiple competing approaches need fair evaluation

Do NOT use when:
- The decision is low-risk and time-sensitive
- Only one valid approach exists

# Operating procedure
1. Define the question and decision criteria
2. Assign 3-5 distinct expert roles (e.g., security, performance, maintainability, user-experience)
3. Have each expert perspective analyze the problem independently
4. Synthesize the perspectives and identify points of agreement and disagreement
5. Make a final decision with rationale referencing the expert inputs

# Output defaults
A panel summary document with each expert perspective, synthesis, and final decision with rationale.

# Failure handling
If expert perspectives conflict irreconcilably, escalate to a human decision-maker with the full panel summary.
