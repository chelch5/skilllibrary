---
name: ticket-audit
description: Audits ticket state, dependencies, and artifact completeness for inconsistencies or stale transitions. Trigger when the ticket system shows signs of drift or inconsistency. Do NOT use for creating or closing tickets.
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
  tags: [ticket, audit, consistency]
---

# Purpose
Audits the ticket system for state inconsistencies, missing artifacts, broken dependencies, and stale transitions.

# When to use this skill
Use when:
- The ticket system appears inconsistent or out of sync with actual work state
- Preparing for a major workflow milestone and wanting to confirm ticket integrity

Do NOT use when:
- Creating new tickets (use ticket-creator)
- Closing or re-verifying tickets (use backlog-verifier)

# Operating procedure
1. Enumerate all tickets and their current states
2. Check each ticket for required fields (description, acceptance criteria, artifact references)
3. Verify dependency chains are not circular and all referenced tickets exist
4. Flag stale transitions (ticket in-progress for too long, completed with missing artifacts)
5. Produce an audit report with findings and recommended actions

# Output defaults
A ticket audit report with per-ticket findings, dependency map, and recommended corrective actions.

# Failure handling
If a ticket references a non-existent artifact or dependency, flag it immediately and do not assume it is valid.
