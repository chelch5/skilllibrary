---
name: context-summarization
description: Compresses large evidence sets into a handoff-friendly summary without dropping critical facts. Trigger when a large conversation thread or document set needs to be condensed for agent handoff. Do NOT use when full fidelity must be preserved.
source: github.com/gpttalker/gpttalker-agent
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agentic-orchestration-and-autonomy
  priority: P2
  maturity: draft
  risk: low
  tags: [summarization, context, handoff]
---

# Purpose
Compresses large evidence sets, conversation threads, or document collections into concise, handoff-ready summaries that preserve critical facts.

# When to use this skill
Use when:
- A downstream agent needs context that exceeds what fits in one context window
- A session handoff requires a compact brief of prior work

Do NOT use when:
- Full fidelity of the original content is required (e.g., legal or compliance review)
- The content is already concise enough to pass as-is

# Operating procedure
1. Identify the audience and their information needs
2. Extract key facts, decisions, blockers, and action items from the source material
3. Structure the summary with sections: current state, key decisions, open items, next steps
4. Validate that no critical facts were dropped by cross-checking against the source

# Output defaults
A structured summary document in Markdown with clearly labeled sections for current state, decisions, open items, and next steps.

# Failure handling
If source material is too large to process in one pass, chunk it and summarize each chunk, then synthesize the chunk summaries.
