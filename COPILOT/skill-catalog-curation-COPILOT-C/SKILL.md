---
name: skill-catalog-curation
description: "Reviews the library as a whole, merges overlaps, and organizes categories and discoverability. A large skill library needs editorial discipline. Trigger when the task context clearly involves skill catalog curation."
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
  tags: [catalog, curation, organization]
---

# Purpose
Reviews an entire skill library for duplicates, category mismatches, coverage gaps, and quality inconsistencies, then produces a curated catalog with a recommended set of actions to improve the library's coherence and discoverability.

# When to use this skill
Use when:
- The user says "curate the skill catalog", "clean up the skill library", or "what's wrong with this skill set?"
- A library has grown past 20 skills and likely has accumulated overlap, gaps, and inconsistencies
- A new category or domain has been added and existing skills need to be re-organised
- Before publishing a skill library, to ensure it is coherent and defensible

Do NOT use when:
- The goal is to manage a single skill's lifecycle (use `skill-lifecycle-management`)
- The goal is to remove one specific skill (use `skill-deprecation-manager`)
- The library has fewer than 10 skills — curation overhead is not yet warranted

# Operating procedure
1. **Inventory the library**: List all skills with their name, category, description (first sentence), and maturity. Build a table or flat list
2. **Detect duplicates and near-duplicates**: Compare skill descriptions for semantic overlap. Flag pairs where two skills appear to do the same thing. Check: do their "When to use" sections conflict or overlap significantly?
3. **Detect category mismatches**: Is each skill in the most accurate category? Skills that span categories signal a splitting or reclassification need
4. **Detect coverage gaps**: Are there common tasks in the library's domain that no skill covers? Look for tasks that users would naturally request but would find no skill for
5. **Assess quality distribution**: Count how many skills are `stable`, `draft`, `deprecated`. Flag skills that have been in `draft` for more than one release cycle without progression
6. **Generate curation actions** for each finding:
   - **Merge**: Two skills should become one (name the survivor)
   - **Split**: One skill is doing too much (name the two new skills)
   - **Reclassify**: Move to a different category
   - **Fill gap**: New skill needed for X
   - **Retire**: Skill is superseded or unused (use `skill-deprecation-manager`)
   - **Promote**: Skill is stable enough to advance from draft
7. **Prioritise actions**: Merges and fills of high-traffic gaps first, cosmetic reclassifications last

# Output defaults
A **Library Inventory** table, a **Findings** list grouped by type (duplicates, gaps, category issues, quality issues), and a **Curation Action Plan** ordered by priority.

# Failure handling
If the library structure is non-standard (no categories, no frontmatter), note what metadata is missing and provide a best-effort inventory based on directory names and SKILL.md content.
