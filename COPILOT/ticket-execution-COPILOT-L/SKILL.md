---
name: ticket-execution
description: "Defines the required stage order, artifact proofs, and routing rules for ticket work. This is the core anti-drift execution contract. Trigger when the task context clearly involves ticket execution."
source: github.com/gpttalker/opencode-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P0
  maturity: draft
  risk: low
  tags: [execution, tickets, workflow]
---

# Purpose
Executes a single ticket through defined stages with verification gates between each phase. Implements the Shape Up "hill chart" model: work moves from unknown (uphill/figuring out) to known (downhill/executing) to done. Each transition requires artifact proof—no stage advances on status alone.

# When to use this skill
Use when:
- Picking up a ticket from the backlog to implement
- Resuming work on an in-progress ticket after context switch
- Verifying a ticket is genuinely complete before marking done

Do NOT use when:
- Creating tickets (use ticket-pack-builder)
- Reviewing/auditing completed work (use review-audit-bridge)
- Multiple tickets need parallel coordination (use workflow-observability first)

# Operating procedure

## Stage 1: Claim & Orient (→ in_progress)
1. **Check preconditions**:
   ```bash
   # Verify no blocking dependencies
   grep "depends_on:" tickets/TKT-XXX.md
   # For each dependency, confirm status: done
   ```
2. **Update ticket status**:
   ```yaml
   status: in_progress
   started: [ISO timestamp]
   assignee: [agent-id or human]
   ```
3. **Create working branch**:
   ```bash
   git checkout -b tkt-XXX-[short-description]
   ```
4. **Read ticket fully**: acceptance criteria, constraints, linked context.

## Stage 2: Uphill (figuring out what to do)
This phase ends when you can enumerate all remaining tasks. Work is "uphill" when unknowns remain.

1. **Identify unknowns**: List what you don't yet know how to do.
2. **Investigate**: Read relevant code, run experiments, ask clarifying questions.
3. **Update ticket with findings**:
   ```markdown
   ## Investigation Notes
   - [Finding 1]
   - [Finding 2]
   
   ## Approach
   [Describe chosen implementation approach]
   
   ## Task Breakdown
   - [ ] Task 1
   - [ ] Task 2
   ```
4. **Gate**: Cannot proceed to Stage 3 until task breakdown exists.

## Stage 3: Downhill (executing known work)
All unknowns resolved. Pure execution.

1. **Work through task breakdown**: Check off items as completed.
2. **Commit incrementally**: Each logical change gets a commit.
   ```bash
   git commit -m "tkt-XXX: [what changed]"
   ```
3. **Run verification continuously**:
   ```bash
   npm test  # or equivalent
   npm run lint
   ```
4. **Update progress in ticket**: Note completed tasks.

## Stage 4: Verification (→ review)
1. **Self-check against acceptance criteria**: Each criterion must have evidence.
   ```markdown
   ## Acceptance Evidence
   - [x] Criterion 1: [how verified, e.g., "test in tests/auth.test.ts"]
   - [x] Criterion 2: [screenshot, log output, etc.]
   ```
2. **Run full test suite**: Must pass.
3. **Update ticket status**:
   ```yaml
   status: review
   completed: [ISO timestamp]
   ```
4. **Open PR if applicable**:
   ```bash
   gh pr create --title "TKT-XXX: [title]" --body "Closes TKT-XXX"
   ```

## Stage 5: Done (→ done)
Only after review approval or self-verification for solo work:
1. **Merge branch**:
   ```bash
   git checkout main && git merge --no-ff tkt-XXX-*
   ```
2. **Update ticket**:
   ```yaml
   status: done
   merged: [ISO timestamp]
   ```
3. **Update BOARD.md**: Move ticket to Done column.

## Parallelization Rules
- **Safe to parallelize**: Independent tickets touching different files/modules
- **Must serialize**: Tickets with shared dependencies, tickets modifying same files
- **Never parallelize**: Tickets where one's output is another's input

# Output defaults
Ticket file updated with:
- Status transitions with timestamps
- Investigation notes (if applicable)
- Task breakdown with checkboxes
- Acceptance evidence
- Link to PR/commit

# References
- Shape Up Hill Chart concept: https://basecamp.com/shapeup/3.4-chapter-13
- "Work is like a hill": uphill = figuring out, downhill = executing

# Failure handling
- **Blocked by dependency**: Set `status: blocked`, add `blocked_by: TKT-YYY`, notify or wait
- **Acceptance criteria unclear**: Do not guess. Add clarification request to ticket, set `status: blocked`
- **Tests fail after implementation**: Do not mark done. Debug, fix, re-verify
- **Scope creep during execution**: If new requirements emerge, create new ticket. Do not expand current ticket scope mid-execution
- **Stuck uphill >2 hours**: Flag in ticket, request help or pair. Do not thrash in circles
