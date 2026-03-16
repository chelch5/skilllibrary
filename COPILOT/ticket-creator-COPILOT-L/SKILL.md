---
name: ticket-creator
description: Creates follow-up tickets only from actual evidence, not vague intentions or duplicated complaints. Trigger when verified findings or gaps need to be tracked as tickets. Do NOT use to create tickets speculatively or without concrete evidence.
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
  tags: [tickets, creation, evidence-based]
---

# Purpose
Creates well-formed follow-up tickets grounded in concrete evidence, preventing speculative or duplicate ticket proliferation.

# When to use this skill
Use when:
- A review, audit, or investigation produced concrete findings that need tracking
- A code review or security review identified actionable issues

Do NOT use when:
- Creating tickets speculatively without evidence
- Duplicating an existing open ticket

# Operating procedure
1. Review the source evidence (review findings, audit report, investigation output)
2. For each distinct, actionable finding, draft a ticket with: title, description, evidence reference, and acceptance criteria
3. Check for duplicates against existing open tickets before creating
4. Assign priority based on severity and impact of the finding
5. Submit tickets and link them to the source evidence

# Output defaults
A set of well-formed tickets in the project's ticket format, each with a link to the source evidence.

# Failure handling
If a finding is ambiguous or not clearly actionable, flag it as "needs clarification" rather than creating a vague ticket.
