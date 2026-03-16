---
name: context-management-memory
description: Manages context window utilization and persists important facts across sessions using structured memory stores. Trigger when working on long projects where important information must survive beyond a single context window. Do NOT use for ephemeral tasks that need no memory.
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
  tags: [context, memory, persistence]
---

# Purpose
Manages context window consumption and persists critical facts to durable memory stores so information survives context resets and session boundaries.

# When to use this skill
Use when:
- A project spans multiple sessions and key facts must be remembered
- Context window is approaching limits and prioritization is needed

Do NOT use when:
- The task is short and fits comfortably in one context window
- No facts need to persist beyond the current session

# Operating procedure
1. Identify facts that are worth persisting (decisions, constraints, key discoveries)
2. Write them to a structured memory store (session database, facts file, or handoff brief)
3. At context boundary, summarize current state and flush to memory
4. At session start, read from memory before beginning work

# Output defaults
A memory store artifact (structured Markdown or JSON) containing persisted facts, decisions, and context summaries.

# Failure handling
If the memory store is unavailable, generate an in-session summary and flag that persistence is degraded. Resume with best available context.
