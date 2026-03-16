---
name: shell-inspection
description: Uses read-only terminal inspection to confirm repo state, file existence, and runtime facts. Trigger when runtime or filesystem verification is needed before acting. Do NOT use to make changes or run write operations.
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
  tags: [shell, inspection, read-only]
---

# Purpose
Uses read-only shell commands to verify filesystem state, file existence, and runtime facts before actions are taken.

# When to use this skill
Use when:
- Verifying that expected files or directories exist before referencing them
- Confirming runtime environment facts (installed tools, versions, active processes)

Do NOT use when:
- Making any filesystem or configuration changes
- Running commands with side effects

# Operating procedure
1. Define what facts need to be confirmed (file paths, tool versions, process state)
2. Run read-only shell commands (ls, cat, which, ps, git status) to gather facts
3. Compare findings against expected state
4. Report any discrepancies before proceeding

# Output defaults
A shell inspection report with commands run, outputs, and a pass/fail verdict for each expected fact.

# Failure handling
If a required fact cannot be confirmed (missing file, tool not installed), report it immediately and halt any dependent actions.
