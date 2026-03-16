---
name: reverse-brainstorming
description: "Asks how to make the plan fail, become slow, or become unreliable, then inverts the answers into protections. A practical hole-poking technique. Trigger when the task context clearly involves reverse brainstorming."
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
  tags: [brainstorming, adversarial, critique]
---

# Purpose
Generates protective measures by first asking how to deliberately cause the problem, then inverting each sabotage into a corresponding safeguard.

# When to use this skill
Use when:
- The user says "reverse brainstorm this", "how would we sabotage this?", or "how could we make this fail on purpose?"
- Conventional risk analysis is not surfacing novel risks because the team is too familiar with the plan
- A creative approach is needed to break out of groupthink about what could go wrong
- The user wants to generate specific protective measures, not just a risk list

Do NOT use when:
- The user wants structured risk analysis with likelihood/severity ratings (use `failure-mode-analysis`)
- The user wants to trace a past failure (use `root-cause-analysis`)
- The idea is too abstract to generate concrete sabotage actions

# Operating procedure
1. **State the goal of the plan**: One sentence: "The plan succeeds if [observable outcome]"
2. **Invert the goal**: "How would we guarantee this plan fails / is slow / produces bad output / gets abandoned?"
3. **Generate 10–15 sabotage actions**: Brainstorm concrete, specific ways to cause failure. No filtering yet — be creative and adversarial. Examples: "Delete the test suite on day 1", "Add 5 external dependencies with no SLAs", "Assign the most critical task to the newest member with no documentation"
4. **Group sabotage actions by theme**: Cluster into 3–5 themes (e.g. technical debt accumulation, coordination failure, incentive misalignment, scope expansion, operational blindness)
5. **Invert each sabotage into a protection**: For each sabotage action, write the corresponding safeguard. The inversion is direct: "Delete the test suite" → "Enforce test coverage thresholds in CI that block merge"
6. **Rate protection value**: For each protection, mark it: High value (would prevent multiple failure modes), Medium, or Low (only prevents this specific sabotage)
7. **Select the top 5 protections**: The highest-value protections that are not already in the plan

# Output defaults
A **Sabotage List** grouped by theme, a **Sabotage → Protection** mapping table, and a **Top 5 Protections to Add** section with specific implementation notes.

# Failure handling
If the plan is too vague to generate specific sabotage actions, list the three aspects of the plan that need to be more concrete before reverse brainstorming can be run effectively.
