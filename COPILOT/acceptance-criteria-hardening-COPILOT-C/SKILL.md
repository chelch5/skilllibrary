---
name: acceptance-criteria-hardening
description: "Turns vague success language into observable, testable, decision-complete acceptance criteria. Good acceptance criteria stabilize agents. Trigger when the task context clearly involves acceptance criteria hardening."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: planning-review-and-critique
  priority: P1
  maturity: draft
  risk: low
  tags: [acceptance-criteria, testing, clarity]
---

# Purpose
Converts vague, subjective, or incomplete acceptance criteria into observable, testable, and decision-complete statements that an agent or tester can evaluate without human interpretation.

# When to use this skill
Use when:
- The user says "harden these AC", "make these testable", or "are these criteria good enough?"
- A ticket has acceptance criteria that contain words like "works correctly", "is fast", "looks good", or "handles errors"
- An agent is expected to self-evaluate completion and needs unambiguous criteria
- A QA or review cycle is about to start and criteria need to be clear before work is assessed

Do NOT use when:
- No acceptance criteria exist yet (write them from scratch using `planning` skill first)
- The criteria are already observable and testable — nothing to improve
- The scope of the ticket is unclear — fix scope first

# Operating procedure
1. **Identify vague language patterns**: Scan each criterion for: subjective adjectives ("good", "clean", "fast"), undefined comparatives ("faster than before"), passive ambiguity ("errors are handled"), and scope gaps (what does "complete" mean for this feature?)
2. **For each vague criterion, apply the SMART rewrite**:
   - **Specific**: What exact behaviour, output, or state must be observable?
   - **Measurable**: What is the threshold? (latency in ms, error rate in %, count of items)
   - **Actor-explicit**: Who does the action that triggers the criterion? (user, system, agent)
   - **Result-explicit**: What is the observable outcome? (what appears, what is stored, what is returned)
   - **Test-able**: Could a script or checklist verify this without human judgement? If not, rewrite until it can
3. **Add negative cases**: For each criterion, add one "does NOT" statement — what the system must NOT do under the same conditions (e.g. "does not show spinner for >500ms")
4. **Add edge cases**: For each criterion, identify the most important boundary condition and add it explicitly (empty input, max load, invalid data)
5. **Check completeness**: Are there implicit "done" states that are not covered by any criterion? Add them
6. **Flag decision gaps**: If a criterion requires a product decision that has not been made (e.g. "what counts as a successful import?"), mark it as **Needs Decision** rather than guessing

# Output defaults
The original criteria followed by the hardened rewrite for each, using a before/after format. A **Decision Gaps** list for items that cannot be hardened without product input.

# Failure handling
If the ticket scope is undefined, the AC cannot be meaningfully hardened. State which scope definition is needed before rewriting.
