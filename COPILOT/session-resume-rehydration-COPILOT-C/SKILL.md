---
name: session-resume-rehydration
description: Restores enough project state for work to resume cleanly after interruption, host change, or model swap. Trigger at the start of a new session when prior context is unavailable. Do NOT use within a continuous uninterrupted session.
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
  tags: [session, rehydration, continuity]
---

# Purpose
Reconstructs the essential project and workflow state needed to resume autonomous work after a session break, host change, or model swap.

# When to use this skill
Use when:
- Starting a new session after an interruption to a long-running workflow
- Switching between AI hosts or models mid-project

Do NOT use when:
- The session is already continuous and context is fresh
- Starting a brand-new project with no prior state to restore

# Operating procedure
1. Locate and read the most recent session state artifact (tickets, handoff brief, last checkpoint)
2. Identify the current workflow stage and the last verified completion point
3. Summarize open work, blockers, and pending decisions
4. Validate state consistency before resuming execution

# Output defaults
A session rehydration summary with current stage, open tickets, last checkpoint, and resume instructions.

# Failure handling
If no state artifact is found, generate a minimal context from repo structure and README. Flag the gap and request human confirmation before proceeding.
