---
name: skill-deprecation-manager
description: "Retires or merges obsolete skills while preserving backward references and library clarity. Large libraries decay quickly without a retirement policy. Trigger when the task context clearly involves skill deprecation manager."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P2
  maturity: draft
  risk: low
  tags: [deprecation, lifecycle, retirement]
---

# Purpose
Deprecates or retires a specific skill safely: updating its state, adding deprecation notices, redirecting any references to it, and preserving the skill's content for historical record without leaving it active in the library.

# When to use this skill
Use when:
- The user says "deprecate this skill", "retire this skill", or "this skill is being replaced by X"
- A skill catalog curation identified a skill for retirement
- A skill has been superseded by a new version or merged into another skill
- A skill is causing harm (misfiring, producing wrong outputs) and must be pulled immediately

Do NOT use when:
- The skill needs to be improved, not retired (use `skill-refinement`)
- Multiple skills need lifecycle management (use `skill-lifecycle-management`)
- The skill is in a repo that does not support deprecation metadata — delete it directly

# Operating procedure
1. **Confirm the deprecation decision**: State the reason. One of: superseded by [skill name], merged into [skill name], unused for [N cycles], consistently failing evaluation, or causing harm
2. **Find all references to this skill**: Search for the skill name in: AGENTS.md, other SKILL.md files (in "Do NOT use when" sections or references), skills-lock.json, documentation, command files
3. **Update each reference**: Replace references to the deprecated skill with either the replacement skill name or a note that no replacement exists
4. **Update the skill's frontmatter**:
   - Set `metadata.maturity` to `deprecated`
   - Add a `deprecated_by` field pointing to the replacement (or "none")
   - Add a `deprecated_reason` field with one sentence
5. **Add a deprecation notice to the SKILL.md body** (top of the file, before Purpose):
   ```
   > ⚠️ DEPRECATED: This skill is deprecated as of [date]. Use [replacement skill] instead.
   > Reason: [one sentence]. This file is kept for reference only.
   ```
6. **Move to archive** (if the library has an archive): Move the skill folder to `ARCHIVE/SKILLNAME/` or equivalent. Do not delete — preserve for reference
7. **Update skills-lock.json** (if applicable): Mark the skill as `deprecated` in the lock file so installers do not use it
8. **Update the library index**: Remove from the active catalog, add to a "Deprecated" section if one exists

# Output defaults
Updated SKILL.md with deprecation notice, a **Reference Update Report** (list of files updated and how), and a confirmation that the skill is in the correct archive location.

# Failure handling
If active workflows depend on the skill and no replacement exists, do not deprecate immediately. Document the dependency and the gap it creates, then recommend using `skill-authoring` to create a replacement first.
