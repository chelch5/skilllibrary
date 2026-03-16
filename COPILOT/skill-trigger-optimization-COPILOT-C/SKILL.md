---
name: skill-trigger-optimization
description: "Improves trigger phrases, descriptions, and routing language so a host actually invokes the skill when it should. Important because undertriggering was called out repeatedly. Trigger when the task context clearly involves skill trigger optimization."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: meta-skill-engineering
  priority: P1
  maturity: draft
  risk: low
  tags: [triggers, routing, optimization]
---

# Purpose
Rewrites a skill's description, trigger phrases, and routing language to increase trigger recall (the skill fires when it should) while maintaining precision (it does not fire when it should not).

# When to use this skill
Use when:
- A skill exists but is consistently not being invoked on appropriate prompts (undertriggering)
- A skill is firing on prompts that should route to a different skill (overtriggering)
- The user says "this skill never triggers", "why isn't this skill being used?", or "the skill fires too often"
- A skill evaluation (from `skill-evaluation`) shows poor routing accuracy

Do NOT use when:
- The skill's procedure is broken — fix the skill body, not just the trigger
- The skill is triggering correctly and the issue is output quality
- The frontmatter description is the only problem and the skill body is fine — just rewrite the description

# Operating procedure
1. **Diagnose the trigger failure mode**:
   - **Undertrigger**: The description is too narrow, uses jargon the user would not use, or requires the user to know the skill exists
   - **Overtrigger**: The description is too broad, overlaps with a sibling skill, or lacks discriminating language
2. **Collect 5 real or realistic prompts** that should trigger this skill — write them as a user would actually phrase the request
3. **Read the current description through a routing model's lens**: Would a routing model, reading only the description, select this skill for each of those 5 prompts?
4. **Rewrite the frontmatter description** using these rules:
   - Lead with the most discriminating signal words (the specific verbs/nouns that distinguish this skill from similar ones)
   - Include 2–3 natural-language trigger phrases a user would actually say, in quotes
   - State the primary use case in the first sentence — not a capability statement but a trigger statement
   - Keep it under 60 words
5. **Rewrite the "When to use" section**: Each bullet must be a specific phrase or condition. Replace "when the user or repo work clearly involves X" with "when the user says 'X'" or "when [specific observable condition]"
6. **Update "Do NOT use when"**: Ensure it names the correct alternative skill for each confusion case
7. **Verify the rewrite against the 5 test prompts**: Would the new description correctly route all 5?

# Output defaults
The rewritten frontmatter description and updated "When to use" / "Do NOT use when" sections, with a **Trigger Test Results** table showing the 5 test prompts and whether the new description routes them correctly.

# Failure handling
If the skill's scope is itself ambiguous (it tries to do two different things), the trigger cannot be optimised until the scope is resolved. Recommend `skill-variant-splitting` before optimising.
