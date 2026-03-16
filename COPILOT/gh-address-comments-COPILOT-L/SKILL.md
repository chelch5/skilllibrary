---
name: gh-address-comments
description: A GitHub-focused skill for methodically addressing PR review comments with evidence-based responses. Use when working through reviewer feedback on a pull request.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: external-reference-seeds
  priority: P2
  maturity: draft
  risk: low
  tags: [github, pull-request, code-review, comments]
---

# Purpose
A GitHub-focused skill for methodically addressing PR review comments with evidence-based responses.

# When to use this skill
Use when:
- Addressing reviewer comments on a GitHub pull request
- Systematically resolving PR review feedback
- Tracking which review comments have been addressed

Do NOT use when:
- Initial PR creation (different workflow)
- Non-GitHub code review workflows

# Operating procedure
1. List all open review comments
2. Categorize by type (code change, question, nitpick)
3. Address each comment with code change or explanation
4. Mark resolved comments with reply linking to commit
5. Re-request review when all comments addressed

# Output defaults
Code changes, comment responses, and resolved comment tracking

# Failure handling
If a comment is unclear, ask for clarification before acting. Don't guess reviewer intent.
