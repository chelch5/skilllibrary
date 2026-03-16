---
name: approval-gates
description: Introduces explicit stop/go gates before implementation, release, destructive mutation, or architectural pivots. Trigger when an autonomous workflow is about to take a high-risk action. Do NOT use for routine read-only or reversible operations.
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
  tags: [approval, gates, safety]
---

# Purpose
Inserts explicit approval checkpoints before irreversible, high-risk, or architecturally significant actions in autonomous workflows.

# When to use this skill
Use when:
- An agent is about to perform a destructive, irreversible, or externally-visible operation
- An architectural pivot or major refactor requires human sign-off before proceeding

Do NOT use when:
- Operations are read-only or easily reversible
- The gate would be purely ceremonial with no real risk to gate against

# Operating procedure
1. Classify the pending action by risk tier (low / medium / high / critical)
2. For medium+ actions, generate a summary of what will change and why
3. Pause execution and surface the gate summary to the approver
4. Resume only on explicit approval; abort and log on rejection or timeout

# Output defaults
A gate summary document with action description, risk level, diff preview, and approve/reject options.

# Failure handling
If no approval is received within a defined timeout, default to abort. Log the gate event regardless of outcome.
