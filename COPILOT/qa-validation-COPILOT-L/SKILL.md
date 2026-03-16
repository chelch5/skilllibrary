---
name: qa-validation
description: Checks whether implemented work meets acceptance criteria from a tester perspective. Use after code review when verifying the feature behaves correctly end-to-end. Do NOT use for code-level review (use `code-review`) or security audits (use `security-review`).
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
  tags: [qa, validation, acceptance, testing]
---

# Purpose
Validates that implementation meets the acceptance criteria defined in the ticket from a QA/tester perspective.

# When to use this skill
Use when:
- Code review is complete and acceptance criteria need verification
- A feature needs end-to-end behavioural validation before closing
- Test coverage gaps need identifying

Do NOT use when:
- The task is code-level review (use `code-review`)
- Security vulnerabilities are the primary concern (use `security-review`)

# Operating procedure
1. Read the acceptance criteria from the ticket
2. Map each criterion to a test scenario
3. Verify each scenario passes or flag it as failing with evidence
4. Check edge cases not covered by the happy path
5. Report pass/fail per criterion with a summary verdict

# Output defaults
Acceptance criteria checklist with pass/fail per item, plus a summary verdict (ready to close / needs fixes).

# Failure handling
If acceptance criteria are missing, request them before proceeding. If tests cannot be run, report which criteria are unverifiable.
