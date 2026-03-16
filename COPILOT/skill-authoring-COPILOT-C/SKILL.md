---
name: skill-authoring
description: "Creates or updates project-local skills inside a generated repo using the repo's own conventions and evidence. Necessary if repos are supposed to evolve their own local intelligence. Trigger when the task context clearly involves skill authoring."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P1
  maturity: draft
  risk: low
  tags: [skill, authoring, local]
---

# Purpose
Creates a new SKILL.md file from scratch that meets quality standards: specific trigger conditions, concrete operating procedures, defined output format, and no boilerplate filler.

# When to use this skill
Use when:
- The user says "write a skill for X", "create a new skill", or "author a skill that does Y"
- A repeated agent task needs to be captured as a reusable skill
- An existing workflow is being formalised into a structured procedure
- A repo's agent team needs a new specialisation

Do NOT use when:
- An existing skill already covers the domain — improve it instead (use `skill-refinement`)
- The task is a one-off that should not become a skill
- The skill domain is too broad to have a single procedure — split first (use `skill-variant-splitting`)

# Operating procedure
1. **Name the skill**: Use a lowercase, hyphenated verb-noun name that states what it does (e.g. `premortem`, `gap-analysis`, `acceptance-criteria-hardening`)
2. **Write the frontmatter block**: Include name, description (routing-optimised — specific trigger language first), source, license, and metadata tags
3. **Write the description for routing**: First clause must contain the most discriminating trigger phrase. End with "Trigger when: [specific condition]". This is what the host reads to decide whether to invoke the skill
4. **Write "When to use" with exact triggers**:
   - Use when: list 2–4 specific phrases a user would say or specific conditions that apply
   - Do NOT use when: list 1–3 cases that look similar but should use a different skill (name the alternative)
5. **Write the operating procedure as numbered steps**: Each step must describe a concrete action, not a vague principle. Steps must be executable by an agent without human interpretation
6. **Write output defaults**: Specify the exact format, structure, or sections the skill produces. If the output has a named artifact (table, list, document), describe it
7. **Write failure handling**: For the most common input failure (too vague, missing data, wrong scope), state exactly what to do
8. **Validate against anti-patterns** (use `skill-anti-patterns` checklist):
   - No step that says "Keep the scope explicit" or similar meta-commentary
   - No trigger that says "when the task clearly involves X" — always name specific signals
   - Output defaults must be concrete, not "structured markdown artifact(s)"

# Output defaults
A complete SKILL.md file with frontmatter, Purpose, When to use (with Do NOT use), Operating procedure (numbered, concrete steps), Output defaults, and Failure handling sections.

# Failure handling
If the domain of the skill is unclear or overlaps heavily with an existing skill, name the overlap and ask whether to replace, extend, or split before writing.
