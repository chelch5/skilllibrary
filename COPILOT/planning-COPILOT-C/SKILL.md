---
name: planning
description: "Turns a ticket or objective into a bounded plan with dependencies, unknowns, and acceptance criteria before implementation starts. Your own reports called out planning as a missing high-value skill. Trigger when the task context clearly involves planning."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P0
  maturity: draft
  risk: low
  tags: [planning, tickets, dependencies]
---

# Purpose
Decomposes a goal, ticket, or objective into a structured, executable plan with ordered tasks, explicit dependencies, defined acceptance criteria, and identified unknowns.

# When to use this skill
Use when:
- The user says "plan this", "break this down", "create a plan for X", or "decompose this ticket"
- A goal is stated but the path to achieving it is unclear or undocumented
- An implementation is about to start and the approach needs to be made explicit before code is written
- A complex feature or migration needs to be sequenced correctly before tickets are created

Do NOT use when:
- A plan already exists and needs review (use `plan-review`)
- The task is small enough to execute directly without planning (single-file change, one-step task)
- The objective itself is unclear — clarify the goal before planning

# Operating procedure
1. **Restate the goal**: Write one sentence: "This plan delivers [observable outcome] for [who] by [constraint]." If any part is unclear, ask before proceeding
2. **Identify constraints**: Timeline, tech stack, existing repo state, team size, out-of-scope items — make these explicit
3. **Decompose into tasks**: Break the goal into the smallest tasks that have clear completion states. Each task should be executable by one agent or person in one sitting
4. **Order by dependency**: Identify which tasks block others. Build a dependency graph (or ordered list with "depends on T[n]" notation). Parallelise where possible
5. **Identify the critical path**: The sequence of blocking tasks that determines total duration. Name it explicitly
6. **Write acceptance criteria for the goal**: Observable, testable statements that confirm the plan is done. Apply `acceptance-criteria-hardening` logic — no subjective language
7. **Write acceptance criteria per task** (for complex tasks): Each task that is non-trivial gets its own done condition
8. **List knowns and unknowns**: What is confirmed? What needs investigation during execution? What could cause the plan to change?
9. **Identify risks**: Top 3 things most likely to cause the plan to fail or overrun (brief — not a full premortem)

# Output defaults
A structured plan with: Goal statement, Constraints, Task list with dependencies and done conditions, Critical path, Goal-level acceptance criteria, Knowns/Unknowns, and Top 3 Risks.

# Failure handling
If the goal cannot be restated in a single clear sentence, the objective is not yet defined enough to plan. Return with the specific questions that must be answered before planning can begin.
