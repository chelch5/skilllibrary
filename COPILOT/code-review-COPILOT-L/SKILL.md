---
name: code-review
description: Reviews implementation for correctness, regressions, maintainability, and alignment with the approved plan. Use when completing a ticket or PR and needing a structured quality gate. Do NOT use for QA acceptance testing or security audits — those have dedicated skills.
source: github.com/gpttalker/agent-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P1
  maturity: draft
  risk: low
  tags: [code-review, quality, correctness, maintainability]
---

# Purpose
Reviews code changes for correctness, regressions, maintainability, and fidelity to the approved plan before a ticket is closed.

# When to use this skill
Use when:
- A ticket implementation is complete and ready for review
- A PR needs a structured quality gate before merge
- The agent needs to check for logic errors, edge cases, or plan drift

Do NOT use when:
- The task is acceptance/QA testing (use `qa-validation`)
- The task is security-focused (use `security-review`)
- The ticket is not yet implemented

# Operating procedure
1. Read the ticket or plan to understand expected behaviour
2. Diff the implementation against the plan — flag any scope creep or missing items
3. Check for logic errors, off-by-one errors, null/edge cases
4. Check for regressions against existing tests or documented behaviour
5. Flag maintainability issues: naming, complexity, missing comments on non-obvious logic
6. Produce a prioritised finding list: blockers → warnings → suggestions

# Output defaults
Numbered finding list with severity (blocker / warning / suggestion), file and line reference, and a one-line fix note. No fixing — review only.

# Failure handling
If the diff is too large to review in one pass, split by module. If the plan is missing, request it before proceeding.
