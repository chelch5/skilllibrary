---
name: skill-reference-extraction
description: "Pulls large docs, examples, and schemas out of the main SKILL body into references for progressive disclosure. This follows the recommended architecture pattern. Trigger when the task context clearly involves skill reference extraction."
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
  tags: [references, extraction, architecture]
---

# Purpose
Moves large embedded content (schemas, examples, reference tables, long glossaries) out of the SKILL.md body into a `references/` folder so the skill body remains focused and the references are available for progressive disclosure when needed.

# When to use this skill
Use when:
- A SKILL.md file is longer than 200 lines because it contains large examples, schemas, or reference tables inline
- The user says "extract references from this skill", "move the examples out", or "slim down this skill"
- A skill body is hard to read because reference content drowns out the operating procedure
- A skill's examples or schemas need to be shared with other skills

Do NOT use when:
- The skill body is the right length and has no large embedded content to extract
- The "large" content is actually the operating procedure itself — do not extract steps into references
- The skill is small enough that a `references/` folder would be over-engineering

# Operating procedure
1. **Identify extraction candidates**: In the SKILL.md body, flag:
   - Inline schemas or data structures longer than 10 lines
   - Inline examples longer than 15 lines
   - Reference tables that are looked up rather than read procedurally
   - Glossary sections longer than 8 entries
   - Any embedded document that is cited rather than read as part of the procedure
2. **Create the `references/` directory**: `SKILLNAME/references/`
3. **For each extraction candidate**:
   - Create a named file in `references/`: `SKILLNAME/references/CONTENT-NAME.md` (or `.json`, `.yaml` as appropriate)
   - Move the content verbatim into the reference file
   - Add a header to the reference file: `# [Title]` and a one-line description of what this reference is for
4. **Replace the extracted content in SKILL.md**: Replace the inline content with a short reference pointer:
   - Example: "See `references/output-schema.json` for the full output format"
   - Example: "Example input/output pairs are in `references/examples.md`"
5. **Verify the skill body is still complete**: The operating procedure must still be fully executable from SKILL.md alone. References are supplements, not required reading for the procedure
6. **Update the manifest** (`manifest.json` if it exists): Add the new reference files to the `files` list

# Output defaults
Modified SKILL.md with reference pointers, a populated `references/` directory with named reference files, and a **Extraction Summary** listing what was moved and why.

# Failure handling
If removing the content makes the operating procedure incomplete or ambiguous, the content is part of the procedure, not a reference. Do not extract it. Document this distinction.
