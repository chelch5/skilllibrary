---
name: docs-handoff
description: Synchronises documentation and handoff surfaces after a ticket or milestone is complete. Use when closing out work that needs README, changelog, or decision-log updates. Do NOT use for initial documentation drafting — use `document-writing` instead.
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
  tags: [docs, handoff, changelog, documentation]
---

# Purpose
Keeps documentation and handoff artefacts in sync after implementation work completes.

# When to use this skill
Use when:
- A ticket or milestone is complete and docs need updating
- README, CHANGELOG, or decision log is stale relative to new behaviour
- A handoff brief is needed for the next agent or team member

Do NOT use when:
- Documentation is being written from scratch (use `document-writing`)
- The work is not yet complete

# Operating procedure
1. Identify which surfaces need updating: README, CHANGELOG, ADR, handoff brief
2. Diff the implemented behaviour against current docs
3. Update each surface with minimal, accurate prose
4. Confirm version numbers and dates are correct
5. Produce a handoff summary: what changed, why, and what comes next

# Output defaults
Updated file content or a diff-ready patch. Handoff summary in bullet form.

# Failure handling
If the scope of changes is unclear, request the ticket or plan before updating docs.
