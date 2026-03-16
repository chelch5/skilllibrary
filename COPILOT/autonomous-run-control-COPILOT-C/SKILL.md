---
name: autonomous-run-control
description: Defines how autonomous runs start, checkpoint, pause, recover, and terminate safely. Trigger when launching an extended autonomous workflow. Do NOT use for interactive single-turn sessions.
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
  tags: [autonomous, run-control, lifecycle]
---

# Purpose
Provides a lifecycle protocol for autonomous runs, covering start, checkpoint, pause, recovery, and safe termination.

# When to use this skill
Use when:
- Launching a workflow expected to run for many steps without human interaction
- Implementing checkpoint and recovery logic for a long-running agent process

Do NOT use when:
- The task is short and interactive, expected to complete in one or two turns
- Human is actively steering each step

# Operating procedure
1. Define run parameters: scope, success criteria, abort conditions, and checkpoint interval
2. Write a start checkpoint before any mutations
3. After each major stage, write a checkpoint and verify it is readable
4. On pause or interrupt, flush state and note the resume point
5. On resume, rehydrate from the last checkpoint before continuing

# Output defaults
A run manifest with status, checkpoint history, current stage, and termination reason when complete.

# Failure handling
If a checkpoint fails to write, halt the run immediately. Do not advance without a verified checkpoint.
