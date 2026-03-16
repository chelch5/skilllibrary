---
name: skill-variant-splitting
description: "Decides when one broad skill should be split into stack variants, platform variants, or micro-skills. Critical once a skill starts absorbing too many domains. Trigger when the task context clearly involves skill variant splitting."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: meta-skill-engineering
  priority: P2
  maturity: draft
  risk: low
  tags: [variants, splitting, decomposition]
---

# Purpose
Decides whether an overloaded skill should be split, how to split it, and what each resulting variant should contain — without losing the core procedure that made the original skill valuable.

# When to use this skill
Use when:
- A skill's "When to use" section has grown to cover 6+ different conditions with significantly different procedures for each
- A skill produces inconsistent output depending on the input type because it is handling too many cases
- The user says "this skill does too much", "split this skill", or "make focused versions of this skill"
- A skill's trigger is firing on inputs that need different procedures

Do NOT use when:
- The skill is doing one thing but doing it poorly (use `skill-refinement`)
- The skill overlap is with a different skill, not internal (use `skill-catalog-curation`)
- The difference between cases is minor — shared procedure with minor branching is fine

# Operating procedure
1. **Identify the overload pattern**: Which of these applies?
   - **Input type overload**: The skill handles inputs that are structurally different (e.g. "code review" for PRs vs. entire codebases)
   - **Audience overload**: The procedure changes significantly depending on who is asking
   - **Platform overload**: The steps are different for different platforms/stacks (e.g. Python vs. Rust)
   - **Scope overload**: The skill addresses both a micro task and a macro task that rarely need to be done together
2. **Draw the split boundary**: State explicitly: "Variant A handles [condition] and Variant B handles [condition]. They share [shared logic]"
3. **Extract the shared core**: Identify the steps in the original procedure that apply to ALL variants — this becomes a shared foundation or is duplicated verbatim into each variant
4. **Write the variant-specific procedure**: For each variant, write only the steps that differ from the shared core. Do not repeat the shared steps — reference them or include them in full depending on whether the variants will be standalone files
5. **Name the variants**: Use the naming convention `SKILLNAME-QUALIFIER` where QUALIFIER is the discriminating attribute (e.g. `code-review-pr`, `code-review-codebase`)
6. **Update the original skill**: Either retire it (add a deprecation notice pointing to the variants) or keep it as a dispatcher that routes to the correct variant based on input
7. **Update the catalog**: Add the new variants to the library index, remove or deprecate the original

# Output defaults
A **Split Decision** statement (why to split and where the boundary is), draft frontmatter for each new variant, and a **Migration Note** explaining how to handle the original skill (retire, keep as dispatcher, or archive).

# Failure handling
If the split boundary is unclear — the cases feel different but the procedure is identical — do not split. Document the ambiguity and recommend monitoring usage for 10+ more runs before deciding.
