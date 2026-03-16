---
name: backlog-verifier
description: Re-checks completed work after workflow or process changes and decides which tickets need re-verification. Trigger when the workflow process is updated and historical completions may be invalidated. Do NOT use for verifying new tickets (use verification-before-advance).
source: github.com/gpttalker/gpttalker-agent
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P1
  maturity: draft
  risk: low
  tags: [backlog, verification, re-check]
---

# Purpose
Re-evaluates previously completed work items when workflow or process changes may have invalidated their completion status.

# When to use this skill
Use when:
- The workflow process has been updated and prior completions may not meet new standards
- A batch of tickets need retroactive verification after a process change

Do NOT use when:
- Verifying newly completed tickets (use verification-before-advance)
- The process has not changed and completions are known to be valid

# Operating procedure
1. Identify the process change and what completion criteria changed
2. Scan all completed tickets to determine which were completed under the old criteria
3. For each affected ticket, re-check against the new criteria
4. Mark as re-verified (pass) or flag for rework (fail) with specific gap description

# Output defaults
A re-verification report listing each ticket, old vs new criteria comparison, and re-verification outcome.

# Failure handling
If a ticket cannot be re-verified due to missing artifacts, mark it as blocked and require rework before re-closing.
