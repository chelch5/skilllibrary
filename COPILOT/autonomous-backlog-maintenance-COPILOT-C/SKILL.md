---
name: autonomous-backlog-maintenance
description: Keeps the backlog clean by reclassifying stale, blocked, duplicated, or superseded tickets under defined rules. Trigger on a scheduled basis or when the backlog grows unwieldy. Do NOT use to resolve substantive ticket content disputes.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agentic-orchestration-and-autonomy
  priority: P2
  maturity: draft
  risk: low
  tags: [backlog, maintenance, triage]
---

# Purpose
Automatically maintains backlog health by identifying and reclassifying stale, duplicate, blocked, or superseded tickets according to defined rules.

# When to use this skill
Use when:
- The backlog has grown large and contains tickets that are clearly stale or redundant
- Performing a regular hygiene pass on the ticket system

Do NOT use when:
- Tickets have active disputes about content or priority (escalate to humans)
- The task is to create or implement tickets (use ticket-creator or planner)

# Operating procedure
1. Scan all open tickets for staleness signals (no updates in N days, blocked with no resolution path)
2. Identify duplicates by comparing titles, descriptions, and affected areas
3. Flag superseded tickets that are made obsolete by newer tickets
4. Apply classifications (stale, duplicate, superseded) and propose disposition (close, merge, reprioritize)
5. Commit changes only after generating a summary for human review

# Output defaults
A backlog hygiene report listing tickets examined, classifications applied, and proposed dispositions.

# Failure handling
If a ticket's status is ambiguous, classify it as "needs-review" and include it in the report without closing it automatically.
