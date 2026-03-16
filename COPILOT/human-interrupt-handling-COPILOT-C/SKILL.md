---
name: human-interrupt-handling
description: Explains how the system should react when the user injects new instructions mid-run without corrupting state. Trigger when an autonomous run receives an unexpected human message. Do NOT use for planned approval gates (use approval-gates instead).
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agentic-orchestration-and-autonomy
  priority: P2
  maturity: draft
  risk: low
  tags: [interrupt, human-in-loop, recovery]
---

# Purpose
Provides a safe protocol for incorporating unexpected human instructions mid-run without losing workflow state or corrupting partially completed work.

# When to use this skill
Use when:
- A human injects new instructions or corrections during an active autonomous run
- The workflow must adapt to mid-run scope changes without discarding completed work

Do NOT use when:
- Using a planned approval gate (use approval-gates skill)
- The session is interactive and each turn is human-driven

# Operating procedure
1. Pause execution at the next safe checkpoint
2. Flush current state to the state store
3. Parse the interrupt instruction and classify it (clarification / redirection / abort)
4. For clarifications, update context and resume; for redirections, re-plan from current state; for aborts, gracefully terminate
5. Log the interrupt event with timestamp and instructions received

# Output defaults
An interrupt log entry and updated run manifest showing where the interrupt occurred and how it was handled.

# Failure handling
If the interrupt instruction is ambiguous, ask one clarifying question before acting. Do not guess at intent for significant redirections.
