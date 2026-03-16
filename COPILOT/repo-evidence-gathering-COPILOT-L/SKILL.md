---
name: repo-evidence-gathering
description: Collects focused repository evidence for a specialist without making edits. Trigger when a specialist needs read-only reconnaissance before making changes. Do NOT use when the agent also needs to make edits.
source: github.com/gpttalker/gpttalker-agent
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P2
  maturity: draft
  risk: low
  tags: [evidence, repo, read-only]
---

# Purpose
Performs read-only repository reconnaissance to gather focused evidence for a downstream specialist agent without making any mutations.

# When to use this skill
Use when:
- A specialist agent needs targeted repo evidence before planning or implementing
- Evidence gathering should be isolated from implementation to keep lanes clean

Do NOT use when:
- The agent needs to make changes (use an implementer role instead)
- Evidence is already available in the current context

# Operating procedure
1. Define the evidence scope: what files, patterns, or facts are needed
2. Perform read-only searches (grep, glob, file reads) within the defined scope
3. Compile findings into a structured evidence report
4. Hand off the report to the requesting specialist without making any edits

# Output defaults
A structured evidence report listing files examined, patterns found, and relevant facts extracted.

# Failure handling
If the required evidence cannot be found in the repo, report what was searched and what was missing. Do not infer missing facts.
