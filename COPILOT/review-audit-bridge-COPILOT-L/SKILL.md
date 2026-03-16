---
name: review-audit-bridge
description: "Translates code review, security review, QA, and audit findings into clear blocker logic and follow-up actions. A repo needs one place that formalizes how findings become decisions. Trigger when the task context clearly involves review audit bridge."
source: github.com/scafforge/session
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P0
  maturity: draft
  risk: low
  tags: [review, audit, findings]
---

# Purpose
Translate code review, security review, QA, and audit findings into clear blocker logic, follow-up tickets, and acceptance criteria — preventing review comments from becoming unchecked backlog noise.

# When to use this skill
Use when:
- A PR review has returned comments that need to be triaged and converted to action items
- A security or QA audit has produced a findings report
- Review comments need to be classified as blocking vs. non-blocking before merge
- The user says "turn these review comments into tickets" or "what do I need to fix before merge?"

Do NOT use when:
- There are no review findings to process
- The task is performing the review itself (use code-review agent)

# Operating procedure
1. **Ingest findings**: read the review source (PR comments, audit report, QA notes)
2. **Classify each finding** by severity:
   - **Blocking**: must be resolved before merge/deploy (bug, security issue, broken contract)
   - **Non-blocking**: should be resolved but does not block (style, minor refactor, documentation)
   - **Informational**: no action required (observation, future consideration)
3. **Validate each finding against the code**: look up the referenced file and line; confirm the finding is accurate before creating a ticket
4. **For blocking findings**: create a ticket in `tickets/open/` with the finding as acceptance criteria
5. **For non-blocking findings**: add to a `tickets/open/TECH-DEBT-BATCH.md` (batch, not individual tickets)
6. **For informational findings**: record in `docs/adr/` or discard after logging
7. **Update the PR or review thread**: reference the created ticket IDs for each blocking finding
8. **Emit a triage summary**: `FINDING | SEVERITY | ACTION | TICKET_ID`

# Output defaults
Triage summary table + created ticket files for blocking findings. Non-blocking items batched.

# Failure handling
If a finding references a file or line that no longer exists (stale review), mark as "stale — verify against current code" and do not create a ticket until re-validated.
