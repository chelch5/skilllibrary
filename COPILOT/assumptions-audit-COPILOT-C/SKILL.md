---
name: assumptions-audit
description: "Extracts unstated assumptions from a plan, brief, architecture, or ticket and marks which ones are dangerous. A strong anti-drift and anti-self-deception tool. Trigger when the task context clearly involves assumptions audit."
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
  tags: [assumptions, audit, risk]
---

# Purpose
Surfaces every implicit assumption embedded in a plan, design, or ticket, then classifies which ones are verified, unverified, or dangerous if wrong. Plans fail not because of known risks, but because of assumptions so deeply embedded they are invisible. This skill makes them visible before they cause damage.

The technique draws from assumption mapping in product design (JTBD methodology) and scientific hypothesis testing: every plan is a hypothesis, and every hypothesis rests on assumptions that should be explicit and testable.

# When to use this skill
Use when:
- The user says "audit the assumptions", "what are we assuming here?", "what could we be wrong about?", or "validate our premises"
- A plan is moving from design to execution and hidden assumptions need explicit surfacing
- A retrospective reveals something "went differently than expected"—name the failed assumption
- An architecture or design doc is being reviewed and unstated dependencies need exposure
- A decision was made quickly and the reasoning behind it needs unpacking

Do NOT use when:
- The user wants general risk identification (use `premortem`)
- The user wants logical contradictions between stated claims (use `contradiction-finder`)
- The plan is so early-stage that no meaningful assumptions have been made yet
- The user wants to attack the plan adversarially (use `red-team-challenge`)

# Operating procedure
1. **Read for factual assertions**: Identify every claim presented as fact that is not backed by evidence in the document:
   - "Users will prefer X"
   - "Latency will be under 100ms"
   - "Team has capacity"
   - "Integration will be straightforward"
   - "Requirements are stable"

2. **Read for implicit dependencies**: Identify everything the plan depends on that is not stated:
   - Third-party service availability and SLAs
   - Team skills and availability
   - Data quality and completeness
   - Regulatory or legal approval
   - Budget continuity
   - Infrastructure capacity

3. **Read for scope assumptions**: What has been implicitly excluded?
   - What counts as "done"?
   - Which edge cases are implicitly out of scope?
   - What maintenance or operational burden is assumed away?
   - What happens if requirements change?

4. **Read for behavioral assumptions**: What user, customer, or stakeholder behaviors are assumed?
   - Will users adopt new workflows?
   - Will stakeholders provide timely feedback?
   - Will partners meet their commitments?

5. **Classify each assumption**:
   - **Verified**: Evidence or prior data exists (cite the evidence)
   - **Plausible but unverified**: Reasonable to assume but not yet confirmed
   - **Risky**: If wrong, the plan fails or requires significant rework
   - **Unknown**: Not enough information to evaluate reasonableness

6. **Flag dangerous combinations**: Identify cases where two or more unverified assumptions must both be true for the plan to work. These compound risks are especially dangerous.

7. **Recommend validation actions**: For each Risky or Unknown assumption, state the cheapest, fastest way to verify it before committing resources.

# Output defaults
A table with columns: Assumption | Category | Impact if Wrong | Validation Action

Followed by a **Compound Risk** section if two or more risky assumptions are load-bearing together.

End with a **Validation Priority** list: the 3-5 assumptions that should be validated first, with specific validation methods.

# References
- Christensen, C. et al. "Jobs to Be Done" theory — assumption mapping in product design
- Ries, E. (2011). The Lean Startup — assumption validation through experimentation
- Kahneman, D. (2011). Thinking, Fast and Slow — cognitive biases that hide assumptions

# Failure handling
If the document is too brief to surface meaningful assumptions, list the structural gaps:
- Missing sections (timeline, constraints, success criteria)
- Unstated context (who, why, what's already decided)
- Absent data (baselines, benchmarks, prior attempts)

State which assumption categories cannot be evaluated without these inputs.
