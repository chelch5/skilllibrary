---
name: skill-refinement
description: "Tightens, clarifies, and de-bloats an existing skill after real usage reveals rough edges. You explicitly asked for this and the creator docs support it. Trigger when the task context clearly involves skill refinement."
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
  tags: [refinement, editing, improvement]
---

# Purpose
Improves an existing skill based on real usage evidence: removing steps that do not add value, sharpening vague language, fixing trigger conditions that misfire, and tightening output format.

# When to use this skill
Use when:
- The user says "this skill isn't working well", "refine this skill", or "tighten up this skill"
- A skill has been used in production and specific failure patterns have been observed (wrong triggers, poor output, missing steps)
- A skill is too long, contains redundant steps, or produces verbose output that is not used
- A skill's trigger is misfiring — triggering on wrong inputs or not triggering on correct ones

Do NOT use when:
- The skill needs adaptation to a different context (use `skill-adaptation`)
- The skill needs splitting because it is trying to do too many things (use `skill-variant-splitting`)
- The skill has boilerplate anti-patterns throughout — a full rewrite is faster (use `skill-authoring`)

# Operating procedure
1. **Identify what usage evidence exists**: Has the skill been run? What outputs were produced? What complaints or observations were made? If no usage data, note that refinement is speculative
2. **Apply the skill anti-patterns checklist** (see `skill-anti-patterns`): Flag any present anti-patterns as items to fix
3. **Audit the trigger section**:
   - Are the "Use when" triggers specific enough to discriminate from similar tasks?
   - Are the "Do NOT use when" cases correct and do they name alternatives?
   - Would a host routing agent actually fire this skill on the correct inputs?
4. **Audit each procedure step**:
   - Does each step describe a single, concrete action?
   - Can a step be removed without losing essential output? If so, remove it
   - Is any step vague enough that two agents would interpret it differently? Rewrite it to be unambiguous
5. **Audit the output defaults**:
   - Is the output format described concretely (named sections, tables, specific labels)?
   - Is the output scoped appropriately — not too much, not too little?
6. **Audit failure handling**:
   - Does it cover the most common actual failure, not just a hypothetical one?
7. **Make the changes**: Edit the skill in place. Do not add new steps unless there is a clear gap. The goal is tighter, not longer
8. **Increment the version or update maturity** in frontmatter if the change is substantive

# Output defaults
The refined SKILL.md with changes applied. A brief **Refinement Log** at the end: what was changed, what usage evidence prompted the change, and what remains for future refinement.

# Failure handling
If no usage evidence exists, run through the anti-patterns checklist only and produce a speculative refinement, labelled as such. Do not claim improvements are validated without evidence.
