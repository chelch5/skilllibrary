---
name: steelman
description: "Rebuilds an idea or plan in its strongest plausible form before judging it. You explicitly asked for steelmanning. Trigger when the task context clearly involves steelman."
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
  tags: [steelman, critique, reasoning]
---

# Purpose
Constructs the strongest possible version of an argument, idea, or plan before evaluating it. This is the opposite of strawmanning—you actively improve the argument by assuming the most favorable interpretation of ambiguities, supplying unstated but reasonable premises, and granting assumptions that could plausibly be true. The goal is to defeat the strongest version of the argument, not the weakest.

# When to use this skill
Use when:
- The user says "steelman this", "what's the best case for X", "argue for this position", or "give this a fair hearing"
- An idea was quickly dismissed and deserves evaluation in its strongest form
- A disagreement exists and you need to articulate the opposing position's most compelling version
- You are about to critique something and want to ensure you're attacking the real argument, not a weak version

Do NOT use when:
- The user wants adversarial attack on a plan (use `red-team-challenge`)
- The user wants a balanced comparison of multiple options (use `tradeoff-analysis`)
- The idea is already fully articulated and needs implementation, not evaluation

# Operating procedure
1. **Identify the core claim**: State the argument in one or two sentences as its proponent would state it. Do not insert your own framings.

2. **List the argument's required assumptions**: What must be true for this argument to hold? List each assumption explicitly. Include factual premises, value judgments, and causal claims.

3. **Grant favorable interpretations**: For each ambiguity in the original argument, resolve it in the direction that makes the argument work best. For vague terms, adopt the interpretation most likely to be defensible.

4. **Supply missing premises**: If the argument has logical gaps, fill them with the strongest reasonable premises the proponent might have intended but not stated.

5. **Find supporting evidence**: What data, precedents, analogies, or logical structures most strongly support this version? Cite the best available support, even if you personally disagree.

6. **State conditions of success**: Under what specific circumstances is this argument most compelling? Name the context in which it would be hardest to refute.

7. **Present as Strongest Case**: Output under a clear heading so it is unambiguous this is a steelman, not your endorsement.

8. **Add falsification conditions**: What would have to be false to invalidate even this strongest version? This provides the honest exit ramp for evaluation.

# Output defaults
A section headed **Strongest Case** containing:
- The restated argument in its best form (2-4 sentences)
- Key assumptions it rests on (numbered list)
- Strongest supporting evidence or precedents
- Conditions under which it is most compelling

Followed by **Conditions for This to Be Wrong**:
- What specific facts or values would need to be false to invalidate the steelmanned version

# References
- https://www.lesswrong.com/tag/steelmanning — LessWrong definition and community discussion
- https://www.lesswrong.com/w/ideological-turing-tests — related technique for verifying understanding
- https://www.lesswrong.com/w/least-convenient-possible-world — related technique for stress-testing arguments

# Failure handling
If the idea is incoherent even under the most charitable interpretation—containing genuine logical contradictions that cannot be resolved by any reasonable premise—state this explicitly. Identify the specific contradiction that prevents a coherent steelman from being constructed and explain why no reasonable interpretation can resolve it.
