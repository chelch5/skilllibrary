---
name: premortem
description: "Assumes the project failed and works backward to identify the most likely causes before work starts. Very effective for avoiding obvious future pain. Trigger when the task context clearly involves premortem."
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
  tags: [premortem, risk, planning]
---

# Purpose
Applies Gary Klein's prospective hindsight technique: project forward to a specific future where the project has failed spectacularly, then work backward to identify the causes. Unlike conventional risk analysis which asks "what might go wrong?", the premortem declares "this has already failed" and asks "why?" This shifts participants from advocacy mode to diagnostic mode, making it psychologically safe to surface concerns that would otherwise go unspoken.

# When to use this skill
Use when:
- The user says "pre-mortem this", "what could kill this project?", "stress-test this plan", or "what am I not seeing?"
- A plan is about to be committed and needs adversarial scrutiny before execution
- A large or irreversible decision is being made (migration, launch, architecture change, hiring)
- The team seems over-confident or has not surfaced dissenting views
- Previous projects with similar characteristics have failed and you want to avoid repeating history

Do NOT use when:
- The project has already failed and needs root cause investigation (use `root-cause-analysis`)
- You need failure mode enumeration for a technical system (use `failure-mode-analysis`)
- The user wants a general risk register without a specific project context

# Operating procedure
1. **Set the failure premise**: State explicitly: "It is [6 months / 1 year / end of project] from now. This project has failed. The outcome was [describe the worst plausible outcome given the stated goals—be specific about what failed and how]."

2. **Generate failure causes independently**: Produce 8-12 distinct failure causes, not solutions disguised as risks. Cover these categories:
   - **Technical failure**: The technology didn't work, scaled poorly, or had unforeseen complexity
   - **Coordination failure**: Teams didn't communicate, handoffs broke down, dependencies weren't managed
   - **Wrong assumptions**: Key premises about users, market, data, or behavior turned out false
   - **Timeline collapse**: Scope grew, estimates were wrong, dependencies slipped
   - **Resource starvation**: Budget cut, key people left, competing priorities pulled focus
   - **External shock**: Market shifted, regulation changed, competitor moved, vendor failed
   - **User/market mismatch**: Built the wrong thing, users didn't adopt, problem wasn't real

3. **Score each cause**: Rate each on two axes:
   - **Likelihood**: High (>50%), Medium (20-50%), Low (<20%)
   - **Impact**: High (project fails completely), Medium (major rework required), Low (recoverable setback)

4. **Identify the top 3 killers**: The causes that are both most likely AND highest impact. These are not abstract risks—they are the specific ways this particular project dies.

5. **Propose specific mitigations**: For each of the top 3, write one concrete, actionable change to the plan that reduces the risk. "Improve communication" is not acceptable. "Weekly 15-min sync between backend and infra teams starting in week 2" is acceptable.

6. **Produce the pre-mortem summary**: One paragraph stating: what failure looks like for this project, the three biggest causes, and the three specific mitigations.

# Output defaults
A table of failure causes with columns: Cause | Category | Likelihood | Impact

Followed by a **Top 3 Risks** section with:
- Each risk described in one sentence
- The specific mitigation (concrete action, owner, timing)

Ending with a one-paragraph **Pre-Mortem Summary** suitable for inserting into a plan document.

# References
- https://hbr.org/2007/09/performing-a-project-premortem — Gary Klein's original HBR article describing the technique
- Klein, G. (1998). Sources of Power: How People Make Decisions — academic foundation for prospective hindsight
- https://en.wikipedia.org/wiki/Pre-mortem — overview and variations

# Failure handling
If the plan is too vague to generate meaningful failure causes (missing timeline, unclear deliverables, unstated constraints), identify the 3 key missing details that would be needed to complete the pre-mortem. List them explicitly and request this information before proceeding.
