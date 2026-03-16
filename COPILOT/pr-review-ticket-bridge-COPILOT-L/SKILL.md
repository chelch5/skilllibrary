---
name: pr-review-ticket-bridge
description: "Transforms validated review findings into guarded follow-up tickets without letting comments become unchecked backlog noise. Useful whenever external review or host-side PR analysis feeds back into the local backlog. Trigger when the task context clearly involves pr review ticket bridge."
source: github.com/scafforge/session
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P1
  maturity: draft
  risk: low
  tags: [pr, review, tickets]
---

# Purpose
Transform validated PR review findings into guarded follow-up tickets — ensuring only real, code-verified issues become backlog items, not every passing comment.

# When to use this skill
Use when:
- A PR review has returned and findings need to be converted to actionable tickets
- An automated code review (e.g., from a code-review agent) has produced findings
- The user says "create tickets from the PR review" or "what follow-up work came out of the review?"
- A merged PR had non-blocking issues that should be tracked for future sprints

Do NOT use when:
- The PR is still open and blocking issues need to be fixed before merge (fix them, don't ticket them)
- The review has zero findings
- The findings are already in the backlog

# Operating procedure
1. **Read the review source**: PR comments, code-review agent output, or audit report
2. **Validate each finding against current code** (not the diff — against HEAD):
   - Look up the referenced file and line
   - Confirm the issue still exists in current state
   - If the finding is stale (already fixed or file removed), discard it
3. **For each validated finding, classify**:
   - `bug` — incorrect behavior
   - `security` — vulnerability or data exposure
   - `tech-debt` — suboptimal but not broken
   - `enhancement` — suggested improvement
4. **Create ticket files** only for `bug` and `security` findings (P0/P1)
5. **Batch `tech-debt` and `enhancement` findings** into a single `TECH-DEBT-BATCH` ticket with a checklist
6. **Each ticket must include**: finding text, file:line evidence, acceptance criteria, and link back to PR
7. **Update MANIFEST.json and BOARD.md** to include new tickets

# Output defaults
Individual ticket files for bugs/security + one batch ticket for tech-debt. MANIFEST.json updated.

# Failure handling
If the PR source cannot be read, request the review output be pasted directly. Do not create tickets from memory or inference.
