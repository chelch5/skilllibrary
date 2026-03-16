---
name: subagent-research-patterns
description: Structures how narrow research lanes gather evidence, summarize it, and hand it back without mutating repo state. Trigger when parallel read-only research is needed before a decision point. Do NOT use when the research agent also needs to make changes.
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
  tags: [research, subagent, evidence]
---

# Purpose
Defines safe patterns for launching research sub-agents that gather evidence in parallel without mutating repo state.

# When to use this skill
Use when:
- Multiple research questions need answers before an implementation decision
- Parallel information gathering would speed up a workflow

Do NOT use when:
- Research must also make code or file changes (use an implementer role instead)
- The question can be answered from already-available context

# Operating procedure
1. Define research lanes with a specific question, scope, and output format
2. Launch read-only research agents in parallel, each confined to its lane
3. Collect and synthesize findings into a unified evidence brief
4. Route the brief to the decision-making agent before any mutations occur

# Output defaults
An evidence brief per lane, plus a synthesized summary for the orchestrator.

# Failure handling
If a research lane returns inconclusive results, flag it explicitly in the brief. Do not proceed with assumptions; surface the gap to the orchestrator.
