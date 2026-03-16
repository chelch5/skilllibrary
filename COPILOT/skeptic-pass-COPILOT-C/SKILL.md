---
name: skeptic-pass
description: "Runs a deliberately doubtful review over a proposal to catch optimism bias and hand-wavy claims. A lightweight critique pass for early-stage thinking. Trigger when the task context clearly involves skeptic pass."
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
  tags: [skeptic, critique, review]
---

# Purpose
Reviews a proposal with deliberate scepticism to surface optimism bias, hand-waving, unsupported claims, and wishful thinking before the idea gains too much momentum.

# When to use this skill
Use when:
- The user says "be skeptical about this", "poke holes in this idea", or "what am I missing here?"
- A proposal is in early stages and needs a critical reality check before resources are committed
- The author is too close to the idea and needs external challenge
- A plan is being rubber-stamped and deserves genuine scrutiny

Do NOT use when:
- The user wants a systematic adversarial attack on a finalised design (use `red-team-challenge`)
- The user wants only upside identified (use `steelman`)
- The idea is mature, detailed, and the user wants structured risk analysis (use `premortem`)

# Operating procedure
1. **Read the proposal assuming every optimistic claim is likely wrong**: This is the operating posture — default to scepticism unless evidence is provided
2. **Flag unsupported claims**: Any assertion of fact that has no evidence, no cited source, and no logical derivation. Mark each: "This claim is unsupported. What evidence backs it?"
3. **Identify the strongest version of the proposal**: Before critiquing, state in one sentence what the proposal is trying to achieve and what would need to be true for it to work
4. **Apply the six sceptic lenses**:
   - **Timeline**: Is the schedule based on wishful thinking? What is the track record for similar work?
   - **User behaviour**: Does this assume users will act against their own convenience or habits?
   - **Technical complexity**: Is the hardest part treated as solved or easy?
   - **Dependencies**: Does this rely on third parties acting predictably and quickly?
   - **Incentives**: Are the incentives of all participants actually aligned with the plan's success?
   - **Second-order effects**: What else changes if this works? Are those effects accounted for?
5. **Rank the five most sceptic-worthy items**: The claims or assumptions that are most likely to be wrong and most consequential if they are
6. **End with a verdict**: One of: "Worth pursuing with these caveats", "High risk — needs these specific changes before proceeding", or "Not viable in current form because of [specific reason]"

# Output defaults
A list of **Unsupported Claims**, a **Six Lenses** review section, a ranked **Top 5 Sceptic Items**, and a one-sentence **Verdict**.

# Failure handling
If the proposal is so vague that specific claims cannot be identified, return a list of the three questions that need to be answered before a meaningful sceptic pass can be run.
