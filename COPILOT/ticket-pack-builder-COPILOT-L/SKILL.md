---
name: ticket-pack-builder
description: "Creates a machine-readable backlog with tickets, dependencies, stages, and acceptance criteria. Small tickets are a core anti-drift mechanism in your workflow. Trigger when the task context clearly involves ticket pack builder."
source: github.com/scafforge/session
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P0
  maturity: draft
  risk: low
  tags: [tickets, backlog, planning]
---

# Purpose
Builds a complete, machine-readable ticket system that autonomous agents can execute without re-planning the entire project each session. Produces an index, board view, and individual ticket files with explicit dependencies, acceptance criteria, and size estimates—enabling agents to pick up work, verify completion, and avoid scope drift.

# When to use this skill
Use when:
- Decomposing a project brief into executable work units
- Setting up a new repo's task tracking infrastructure
- Converting a vague feature list into agent-executable tickets

Do NOT use when:
- Executing tickets (use ticket-execution)
- The project already has a functioning ticket system (add tickets individually)
- Doing quick fixes that don't warrant formal tickets

# Operating procedure

## 1. Create directory structure
```bash
mkdir -p tickets
```

## 2. Decompose work into tickets
From `docs/BRIEF.md`, identify discrete work units. Each ticket should be:
- **Small**: 1-4 hours of focused work (not days)
- **Independent**: Minimal dependencies on other tickets
- **Verifiable**: Clear done/not-done criteria
- **Valuable**: Delivers something testable, not just "refactoring"

## 3. Generate TICKET-INDEX.md
```markdown
# Ticket Index

| ID | Title | Status | Priority | Depends On | Size |
|----|-------|--------|----------|------------|------|
| TKT-001 | Set up project structure | todo | P0 | — | S |
| TKT-002 | Implement user auth | todo | P0 | TKT-001 | M |
| TKT-003 | Add login UI | todo | P1 | TKT-002 | S |

## Size Key
- XS: <1 hour
- S: 1-2 hours  
- M: 2-4 hours
- L: 4-8 hours (consider splitting)

## Status Values
- todo: Not started
- in_progress: Being worked on
- review: Complete, awaiting verification
- done: Verified complete
- blocked: Cannot proceed
```

## 4. Generate BOARD.md (Kanban view)
```markdown
# Project Board

## Backlog
- [ ] TKT-003: Add login UI

## Ready (no blockers)
- [ ] TKT-001: Set up project structure

## In Progress
(none)

## Review
(none)

## Done
(none)

---
Last updated: [ISO timestamp]
```

## 5. Generate individual ticket files
For each ticket, create `tickets/TKT-XXX-short-name.md`:

```markdown
---
id: TKT-001
title: Set up project structure
status: todo
priority: P0
size: S
depends_on: []
blocks: [TKT-002, TKT-003]
created: 2024-01-15
---

# TKT-001: Set up project structure

## Description
Initialize the repository with standard directory structure, package.json, and basic configuration files.

## Acceptance Criteria
- [ ] `src/` directory exists with `index.ts`
- [ ] `package.json` has correct name and scripts
- [ ] `tsconfig.json` configured for ES2022
- [ ] `npm install` completes without errors
- [ ] `npm run build` produces output in `dist/`

## Context
- Reference: docs/STACK-PROFILE.md for tech choices
- Related: TKT-002 will build on this structure

## Notes
(Investigation notes, approach decisions added during execution)
```

## 6. Validate dependency graph
```bash
# Check for cycles (pseudo-code)
for each ticket T:
  if T.depends_on contains ticket that depends_on T:
    ERROR: circular dependency
```

## 7. Identify critical path
List tickets that must complete sequentially:
```markdown
## Critical Path
TKT-001 → TKT-002 → TKT-005 → TKT-008
Estimated: 12 hours
```

## 8. Mark nice-to-haves
Following Shape Up convention, prefix optional scope with `~`:
```markdown
## Acceptance Criteria
- [ ] Core login flow works
- [ ] ~Remember me checkbox
- [ ] ~Social login buttons
```

# Output defaults
```
tickets/
├── TICKET-INDEX.md      # Master list with all tickets
├── BOARD.md             # Kanban view
├── TKT-001-project-setup.md
├── TKT-002-user-auth.md
└── TKT-003-login-ui.md
```

# References
- Shape Up "Map the Scopes": https://basecamp.com/shapeup
- Small tickets prevent drift: tasks that can be verified in hours, not days

# Failure handling
- **Brief too vague**: Cannot decompose "build the app" into tickets. Request specific features or user stories first.
- **Ticket too large**: If estimated >4 hours, split into sub-tickets. Use `-a`, `-b` suffixes: `TKT-002-a`, `TKT-002-b`.
- **Circular dependencies**: Refactor tickets to break cycle. Usually means tickets are too coupled—find the shared prerequisite and extract it.
- **No clear acceptance criteria**: Do not create ticket. Flag in DECISIONS.md as needing clarification.
