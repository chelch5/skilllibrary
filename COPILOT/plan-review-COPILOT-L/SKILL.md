---
name: plan-review
description: "Reviews a proposed plan for completeness, sequencing, hidden assumptions, and execution readiness before implementation begins. You explicitly asked for this and GPTTalker already has a plan-review agent. Trigger when the task context clearly involves plan review."
source: github.com/gpttalker/agent-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: planning-review-and-critique
  priority: P0
  maturity: draft
  risk: low
  tags: [plan-review, critique, readiness]
---

# Purpose
Reviews a plan before execution starts to assess whether it is complete enough to begin, correctly sequenced, free of hidden assumptions, and likely to succeed given current constraints.

# When to use this skill
Use when:
- The user says "review this plan", "is this plan ready?", or "check this before we start"
- A plan has been written by a planner agent and needs a second-pass review before execution
- An implementation is about to begin and the plan needs a final sanity check
- A ticket or brief is about to be handed to an implementer and needs to be verified

Do NOT use when:
- The plan is mid-execution and needs progress assessment (use `drift-detection`)
- The user wants only risk analysis (use `premortem`)
- No plan exists — help write one first (use `planning`)

# Operating procedure
1. **Check completeness**: Does the plan have all required sections? Required: goal, acceptance criteria, steps or tasks, dependencies, constraints, and definition of done. Flag any missing sections
2. **Check sequencing**: Are the steps in the correct dependency order? Could any step start before its prerequisites are done? Could any two steps be parallelised but are listed sequentially?
3. **Check acceptance criteria**: Are the success criteria observable and testable? Flag any criterion containing "works correctly", "handles errors", or other subjective language (apply `acceptance-criteria-hardening` logic)
4. **Audit assumptions**: List every implicit assumption in the plan. For each, mark as: Verified, Plausible, or Risky (same as `assumptions-audit` abbreviated pass)
5. **Identify the critical path**: Which sequence of steps determines the minimum timeline? Name the critical path and flag any step on it that is unclear, underespecified, or blocked
6. **Check for missing work**: Is there implicit work not listed? Common omissions: setup/teardown, testing tasks, documentation updates, migration steps, rollback plan
7. **Issue a readiness verdict**: One of:
   - **Ready to Execute**: Plan is complete, sequenced correctly, and assumptions are acceptable
   - **Ready with Caveats**: Executable but specific items need attention during execution (list them)
   - **Not Ready**: Specific blocking gaps must be filled before implementation should begin (list them)

# Output defaults
A structured review with sections: Completeness, Sequencing, Acceptance Criteria Quality, Assumption Audit, Critical Path, Missing Work. End with a one-line **Readiness Verdict** and any **Blocking Issues**.

# Failure handling
If the plan is a rough outline or bullet list without sufficient detail, state the minimum structure required for a meaningful review and return the plan with questions embedded in the gaps.
