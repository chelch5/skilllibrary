---
name: skill-description-optimizer
description: "Improves skill descriptions so routing triggers fire more reliably without overfiring. Your research highlighted undertriggering and the need for pushier descriptions. Trigger when the task context clearly involves skill description optimizer."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P1
  maturity: draft
  risk: low
  tags: [description, routing, optimization]
---

# Purpose
Rewrites the frontmatter `description` field of a skill to maximise routing accuracy: ensuring the description causes a routing model to select this skill for its correct inputs and not select it for inputs belonging to other skills.

# When to use this skill
Use when:
- The user says "optimize the description", "rewrite the skill description for better routing", or "this skill isn't being found"
- A skill evaluation shows low trigger recall (missing fires on correct inputs)
- A batch of skill descriptions needs to be audited and improved for a library release
- The description field contains passive, vague, or purely capability-statement language

Do NOT use when:
- The full "When to use" section also needs rewriting — use `skill-trigger-optimization` for a full trigger overhaul
- The skill's scope is the problem, not the description text
- The description already contains specific trigger phrases and is performing correctly

# Operating procedure
1. **Read the current description**: Note its length, language style (capability statement vs. trigger statement), and discriminating power
2. **Identify the failure mode**:
   - **Undertrigger**: Too narrow, too technical, or does not contain the words a user would naturally use
   - **Overtrigger**: Too broad, overlaps with sibling skills, lacks discriminating terms
   - **Passive**: Describes what the skill *is* rather than when to invoke it
3. **Extract the primary discriminating signals**: What words or phrases, if present in a user prompt, most strongly predict that THIS skill (and not a sibling) should fire? These are typically: specific task verbs ("steelman", "pre-mortem", "red-team"), domain terms, or explicit task names
4. **Write the new description using this structure**:
   - Sentence 1: Lead with the action + the most discriminating signal word(s). Start with a verb or the skill name
   - Sentence 2: State the problem it solves or the context where it applies
   - Sentence 3: One "Trigger when:" clause with a specific natural-language condition
   - Total: 40–70 words. No padding
5. **Check for sibling conflicts**: Read descriptions of the 2–3 most similar skills. Does the new description discriminate correctly from each of them? If a user prompt could match both this and a sibling, add a distinguishing clause
6. **Validate with 5 test prompts**: Does the new description correctly route all 5 positive test cases? Does it avoid matching 3 negative test cases?

# Output defaults
The original description, the rewritten description, a **Discrimination Check** table showing the 2–3 sibling skills and how the new description differs from each, and test prompt routing results (5 positive, 3 negative).

# Failure handling
If the skill's scope is ambiguous or it genuinely overlaps with another skill at the procedure level, the description cannot be fixed by rewording alone. Recommend `skill-variant-splitting` or `skill-catalog-curation` to resolve the underlying overlap.
