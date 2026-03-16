---
name: agent-memory
description: Provides persistent memory storage and retrieval patterns for agents that need to remember facts across sessions. Trigger when an agent needs to store or retrieve information that persists beyond the current context window. Do NOT use for ephemeral in-session information.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P1
  maturity: draft
  risk: low
  tags: [memory, persistence, agents]
---

# Purpose
Defines patterns for agents to store and retrieve persistent memory, enabling consistent behavior across sessions and context resets.

# When to use this skill
Use when:
- An agent needs to remember preferences, decisions, or facts across multiple sessions
- Building an agent that improves or adapts based on accumulated history

Do NOT use when:
- The information only matters within the current session
- No persistence infrastructure is available

# Operating procedure
1. Identify the categories of information worth storing (user preferences, project decisions, learned facts)
2. Choose a storage backend appropriate to the environment (file, database, key-value store)
3. Define read/write patterns: when to write, when to read, and when to expire stale entries
4. Implement retrieval with relevance filtering so the agent gets the most pertinent memories first

# Output defaults
A memory schema definition and read/write procedure documentation.

# Failure handling
If the memory store is unavailable, operate from in-session context only and log that persistence is degraded.
