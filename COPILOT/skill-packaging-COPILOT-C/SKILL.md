---
name: skill-packaging
description: "Packages a skill into installable outputs and validates bundle contents. Needed if you want portable artifacts rather than a loose folder. Trigger when the task context clearly involves skill packaging."
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
  tags: [packaging, bundle, distribution]
---

# Purpose
Assembles a skill folder into a distributable, installable artifact with a validated manifest, correct file structure, and optional checksum — ready for publishing to a registry or sharing as a bundle.

# When to use this skill
Use when:
- The user says "package this skill", "make this skill installable", or "prepare this skill for distribution"
- A skill has been authored or refined and needs to be published to a registry
- A set of skills needs to be bundled into a single installable package
- A skill is being shared with another repo or team and needs a clean, self-contained artifact

Do NOT use when:
- The skill is not yet complete or has not passed a safety review
- The goal is installation into a target repo (use `skill-installation`)
- The goal is to orchestrate packaging of multiple skills (use `skill-packager`)

# Operating procedure
1. **Validate the skill is ready to package**:
   - SKILL.md exists and has complete frontmatter (name, description, source, license, compatibility, metadata)
   - No boilerplate anti-patterns in the body (check against `skill-anti-patterns`)
   - If a `tests/` folder exists, all tests pass (or are marked as expected-fail with explanation)
2. **Verify the directory structure**: The skill folder must contain: `SKILL.md` at minimum. Optional: `tests/`, `references/`, `overlays/`, `examples/`
3. **Generate the manifest file** (`manifest.json` in the skill folder):
   - `name`, `version`, `description` (from frontmatter)
   - `files`: list of all files in the bundle
   - `checksum`: SHA-256 of SKILL.md content
   - `compatibility`: clients list from frontmatter
   - `source` and `license`
4. **Create the zip bundle**: `SKILLNAME-VERSION.zip` containing the skill folder with all files
5. **Validate the bundle**: Unzip to a temp location, verify all listed files are present, verify the manifest checksum matches SKILL.md
6. **Tag the release**: Update `metadata.maturity` from `draft` to `stable` in the frontmatter if the skill has been evaluated

# Output defaults
A `manifest.json` in the skill folder, a `.zip` bundle ready for distribution, and a **Package Validation** report confirming all files present and checksum verified.

# Failure handling
If the skill has missing frontmatter fields or anti-pattern content, list the specific issues that must be fixed before packaging can proceed.
