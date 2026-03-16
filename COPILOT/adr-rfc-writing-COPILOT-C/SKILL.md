---
name: adr-rfc-writing
description: Writes architecture decision records and request-for-comment documents that capture options considered and rationale for decisions. Use to preserve institutional knowledge.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P1
  maturity: draft
  risk: low
  tags: [adr, rfc, architecture, decisions]
---

# Purpose
Writes architecture decision records and request-for-comment documents that capture options considered and rationale for decisions.

# When to use this skill
Use when:
- Documenting an architecture decision with alternatives considered
- Writing an RFC for a proposed system or API change
- Creating a decision log entry after a design discussion

Do NOT use when:
- Routine code changes that don't require architecture decisions
- Meeting notes without a decision outcome

# Operating procedure
1. State the decision or proposal clearly
2. List alternatives considered with pros/cons
3. Document constraints and assumptions
4. Record the decision and rationale
5. Link to related ADRs or RFCs

# Output defaults
ADR or RFC document with decision, context, alternatives, and rationale

# Failure handling
If decision is still open, mark as PROPOSED not ACCEPTED. Avoid premature closure.
