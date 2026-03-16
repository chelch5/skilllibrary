---
name: skill-adaptation
description: "Adapts a general skill so it fits one repo, team, or project profile without losing the base pattern. You explicitly asked for this. Trigger when the task context clearly involves skill adaptation."
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
  tags: [adaptation, profile, customization]
---

# Purpose
Takes a general-purpose skill and modifies its triggers, procedures, and output format to fit the conventions, stack, and constraints of a specific repo or project without losing the core logic.

# When to use this skill
Use when:
- The user says "adapt this skill for our project", "customise this skill for X stack", or "make this fit our workflow"
- A library skill is being installed into a repo that has specific conventions, tools, or naming patterns
- A general skill's output format conflicts with the repo's documentation or ticket system
- The base skill's trigger language does not match how this team describes the task

Do NOT use when:
- The goal is to fix a broken skill (use `skill-refinement`)
- The goal is to split a skill into variants (use `skill-variant-splitting`)
- The skill needs to be rewritten from scratch (use `skill-authoring`)

# Operating procedure
1. **Read the base skill in full**: Identify the core procedure (the steps that must not change) versus the presentation layer (format, trigger phrases, output structure, tool references)
2. **Inventory the target repo context**: What conventions exist? File naming, ticket format, CI tooling, primary language, agent team names. This comes from AGENTS.md, existing skills, and repo structure
3. **Identify the adaptation surface**: Which parts of the skill need changing?
   - **Trigger phrases**: Update to match the language this team actually uses
   - **Tool references**: Replace generic tool names with the repo's actual tools (e.g. "your ticket system" → "Linear", "your CI" → "GitHub Actions")
   - **Output format**: Adjust to match repo conventions (e.g. ADR format, specific header structure, required fields)
   - **Scope constraints**: Add or remove steps that are irrelevant or mandatory for this context
4. **Apply adaptations without corrupting the procedure**: The numbered steps of the operating procedure must remain functionally equivalent. Change language and specifics, not logic
5. **Update the frontmatter**: Change `source` to reference the original, add the repo or profile name to `metadata`, update tags if needed
6. **Write a short adaptation note** at the bottom of the skill: "Adapted from [original] for [repo/team]. Changes: [list of what was changed and why]"
7. **Verify routing still works**: Re-read the description and trigger section. Does it still fire on the right inputs in the new context?

# Output defaults
The adapted SKILL.md with all changes applied, plus an **Adaptation Note** section at the end documenting what changed, what was preserved, and the source skill reference.

# Failure handling
If the target repo conventions are not documented, list what needs to be known before adaptation can be completed (ticket format, tool names, file conventions).
