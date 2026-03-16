---
name: tradeoff-analysis
description: "Compares competing options across cost, complexity, flexibility, risk, and maintenance burden. Useful across stack, model, and architecture choices. Trigger when the task context clearly involves tradeoff analysis."
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
  tags: [tradeoffs, analysis, options]
---

# Purpose
Compares two or more concrete options across the dimensions that actually matter for the decision, then produces a recommendation with explicit reasoning. This is Multi-Criteria Decision Analysis (MCDA) adapted for software and planning decisions: structure the options, define evaluation criteria, score systematically, and make the tradeoffs visible so the decision is defensible.

# When to use this skill
Use when:
- The user says "compare these options", "what are the tradeoffs?", "help me choose between X and Y", or "which should we pick?"
- An architecture, stack, model, framework, or approach choice needs to be made with multiple viable candidates
- A decision needs to be documented (e.g., in an ADR) with the comparison visible
- The user is leaning toward an option but wants the full picture before committing
- Stakeholders disagree and need a structured comparison to align

Do NOT use when:
- There is only one real option (the choice is already made—just implement it)
- The user wants to discover what options exist (do discovery first, then apply this skill)
- The user wants risk identification without option comparison (use `premortem`)
- The user wants to batch multiple decisions (use `decision-packet-builder`)

# Operating procedure
1. **Name the options**: List each option clearly and precisely. If options are vague ("use a better approach"), clarify them before proceeding. Each option must be concrete enough to evaluate.

2. **Define evaluation dimensions**: Start with the default set, then add domain-specific ones:
   
   **Default dimensions**:
   - **Initial cost**: Effort/money to implement
   - **Ongoing cost**: Maintenance, operations, licensing
   - **Complexity**: Build complexity + operational complexity
   - **Flexibility**: How hard to change or extend later
   - **Risk**: Probability × impact of failure
   - **Time to value**: How fast can we get something working

   **Add as relevant**:
   - Performance (latency, throughput, resource usage)
   - Vendor lock-in
   - Team familiarity / learning curve
   - Security posture
   - Scalability ceiling
   - Community/support ecosystem

3. **Score each option per dimension**: Use a consistent scale:
   - Quantitative: 1-5 (1=poor, 5=excellent) OR
   - Qualitative: High/Medium/Low (for clarity over false precision)
   
   Write one sentence explaining each score. Scores without justification are worthless.

4. **Identify dominant options**: Is there any option that is better or equal on every dimension? If so, name it as dominant—the decision is made.

5. **Identify key tensions**: For options without a dominant winner, name the specific dimensions where they trade off:
   - "Option A is cheaper but harder to change later"
   - "Option B is faster to implement but has higher ongoing cost"
   - "Option C scales better but the team has no experience"

6. **Weight by context**: Based on the user's stated priorities (if given), weight dimensions. If the user said "we need to ship fast," weight Time to Value higher. If they said "this must last 5 years," weight Flexibility higher.

7. **State the recommendation**: Pick one option. State it directly. Give 2-3 specific reasons why it wins in this context. Do not hedge with "it depends"—make the call.

# Output defaults
A comparison matrix (options × dimensions) with scores and one-sentence justifications.

A **Key Tensions** section identifying the core tradeoffs.

A **Recommendation** section with:
- The chosen option (named explicitly)
- 2-3 reasons why it wins
- Conditions under which you would choose differently: "If X mattered more, choose Y instead"

# References
- Multi-Criteria Decision Analysis (MCDA) — formal decision theory framework
- Kepner-Tregoe decision analysis — structured decision methodology
- https://en.wikipedia.org/wiki/Multi-criteria_decision_analysis — academic foundations

# Failure handling
If an option is missing critical information to score it:
1. Mark that cell as **Unknown**
2. Note what specific information is needed
3. Proceed with partial analysis
4. Indicate how the recommendation might change if the unknown is resolved favorably/unfavorably
