---
name: red-team-challenge
description: "Actively looks for weak points, exploitation paths, unsafe assumptions, and failure cases in a design or plan. Pairs naturally with plan review. Trigger when the task context clearly involves red team challenge."
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
  tags: [red-team, security, adversarial]
---

# Purpose
Attacks a plan, design, or system from the perspective of an adversary whose goal is to break it, exploit it, or cause it to fail. This technique originates from military and security practice where a "red team" simulates enemy action to find vulnerabilities before real adversaries do. Unlike risk analysis which passively lists concerns, red-teaming actively probes for attack vectors and exploitation paths.

# When to use this skill
Use when:
- The user says "red-team this", "attack this plan", "poke holes in this", "find the weaknesses", or "how would you break this?"
- A security design, auth system, agent workflow, or trust boundary needs adversarial review
- A plan has been approved but needs a final adversarial check before execution
- The goal is to find exploitable weaknesses, not just surface risks (contrast with `premortem`)
- A system handles sensitive data, money, or irreversible actions

Do NOT use when:
- The user wants the strongest case for an idea (use `steelman`)
- The user wants general risk identification without adversarial framing (use `premortem`)
- The document is still in early ideation—attack concrete proposals, not vague ideas
- The user wants to trace a past failure (use `root-cause-analysis`)

# Operating procedure
1. **Define the attack surface**: List the key claims, interfaces, dependencies, assumptions, and trust boundaries in the plan. Identify what must hold for the system to be secure/correct.

2. **Adopt an adversarial role**: Explicitly state: "I am acting as an adversary whose goal is to cause this plan to fail, be exploited, or produce wrong/harmful outcomes."

3. **Run five attack categories**:

   **Assumption attacks**: Which assumptions, if false, break the plan entirely? What happens if "users will behave correctly" is false? If "third-party service will be available" is false? If "team understands the requirements" is false?

   **Interface attacks**: Which integration points, APIs, handoffs, or inputs can be gamed, broken, spoofed, or injected into? Where is input trusted without validation?

   **Resource attacks**: What happens if time, budget, compute, or people are cut by 50%? Which parts fail first? Are there graceful degradation paths?

   **Incentive attacks**: Who benefits from this plan failing? What would a rational actor with misaligned incentives do? Are there gaming opportunities?

   **Edge case attacks**: What valid-but-extreme inputs break expected behavior? What happens at zero, at maximum scale, at boundaries?

4. **Rate each finding**: 
   - **Severity**: Critical (system fails, security breach, data loss) / High (major malfunction) / Medium (degraded function) / Low (minor issue)
   - **Exploitability**: Easy (no special knowledge or access required) / Moderate (requires some knowledge or access) / Hard (requires significant effort or insider access)

5. **Propose specific fixes**: For every Critical or High finding, propose the minimum change that closes the attack vector. Be specific—"add rate limiting to /api/auth endpoint at 10 requests/minute" not "improve security".

# Output defaults
An **Attack Surface** list identifying what must hold for security/correctness.

A findings table with columns: Finding | Attack Category | Severity | Exploitability | Description

A **Critical Fixes Required** section for all Critical and High findings, each with:
- The vulnerability in one sentence
- The specific fix with enough detail to implement

# References
- https://en.wikipedia.org/wiki/Red_team — history and methodology
- Zenko, M. (2015). Red Team: How to Succeed By Thinking Like the Enemy — practitioner's guide
- RAND Corporation red team methodologies — original Cold War applications
- https://github.com/anthropics/anthropic-cookbook — examples of AI system evaluation

# Failure handling
If the plan is incomplete or too abstract to attack:
1. List what is missing that prevents a thorough red-team
2. State which attack categories cannot be evaluated without those details
3. Perform partial analysis on the categories that can be evaluated, clearly marked as incomplete
