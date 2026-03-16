---
name: meeting-notes-decision-log
description: Turns meeting discussions into structured notes and durable decisions rather than loose summaries. Produces actionable outcomes with owners and due dates.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P2
  maturity: draft
  risk: low
  tags: [meeting-notes, decisions, log, documentation]
---

# Purpose
Turns meeting discussions into structured notes and durable decisions rather than loose summaries.

# When to use this skill
Use when:
- Documenting the outcome of a meeting or discussion
- Capturing decisions with owner and rationale
- Creating action items with assigned owners

Do NOT use when:
- Real-time meeting transcription (a different tool)
- General writing without a meeting context

# Operating procedure
1. Capture attendees, date, and meeting purpose
2. List decisions made with rationale
3. Record action items with owner and due date
4. Note open questions and parking lot items
5. Distribute to attendees within 24 hours

# Output defaults
Meeting notes with decisions, actions, owners, due dates, and open questions

# Failure handling
If a decision is contested, record the dispute and schedule a follow-up. Don't paper over it.
