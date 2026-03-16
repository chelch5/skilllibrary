---
name: workflow-state-memory
description: Stores durable workflow state explicitly so agents do not rely on hazy conversational memory. Trigger when a multi-step workflow needs to survive beyond a single context window. Do NOT use for ephemeral single-turn tasks.
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
  tags: [state, memory, persistence]
---

# Purpose
Establishes explicit, durable storage for workflow state so autonomous agents can operate reliably across context boundaries.

# When to use this skill
Use when:
- A workflow spans multiple sessions or context windows
- State must be shared between multiple agents without relying on conversational memory

Do NOT use when:
- The task fits entirely within one context window
- No state needs to persist after the session ends

# Operating procedure
1. Define the state schema (current stage, completed items, open items, decisions made)
2. Write state to a durable artifact (ticket file, JSON store, or session database) after each stage
3. Read state at the start of each session or agent handoff to confirm current position
4. Compact and prune stale state entries to avoid bloat

# Output defaults
A structured state file (JSON or Markdown) at a well-known repo path, updated at each workflow checkpoint.

# Failure handling
If state is corrupt or unreadable, revert to the last valid checkpoint. Alert the orchestrator and do not proceed until state is verified.
