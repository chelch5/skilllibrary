---
name: multi-agent-debugging
description: Diagnoses whether a failure came from the prompt layer, routing, state, tooling, or the agents themselves. Trigger when a multi-agent workflow produces unexpected or incorrect outputs. Do NOT use for debugging single-agent or single-tool failures.
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
  tags: [debugging, multi-agent, diagnostics]
---

# Purpose
Provides a structured diagnostic framework for identifying which layer of a multi-agent system caused a failure.

# When to use this skill
Use when:
- A multi-agent workflow produced wrong outputs or failed unexpectedly
- The failure cause is unclear (prompt, routing, state, or tool layer)

Do NOT use when:
- Debugging a single-agent or single-tool failure in isolation
- The failure cause is already clearly identified

# Operating procedure
1. Collect all available logs, artifacts, and state snapshots from the failed run
2. Isolate the failure to a stage and responsible agent
3. Check each layer: prompt quality, input routing, state correctness, tool availability, agent behavior
4. Form a hypothesis and test it by replaying the failed stage with minimal changes
5. Document the root cause and add a prevention measure

# Output defaults
A diagnostic report with failure timeline, layer analysis, root cause hypothesis, and recommended fix.

# Failure handling
If the failure cannot be isolated to a single layer, produce a ranked list of candidate causes with evidence for each.
