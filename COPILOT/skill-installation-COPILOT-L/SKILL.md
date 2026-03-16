---
name: skill-installation
description: "Installs or links a skill into a target client or local environment using the correct conventions. The skill-installer package in your sources makes this a clear candidate. Trigger when the task context clearly involves skill installation."
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: meta-skill-engineering
  priority: P0
  maturity: draft
  risk: low
  tags: [installation, linking, client]
---

# Purpose
Installs a skill from a source (registry, zip bundle, or local path) into a target project or client, placing files in the correct location and verifying the installation is functional.

# When to use this skill
Use when:
- The user says "install this skill", "add this skill to my project", or "set up this skill in [client]"
- A skill needs to be added to a repo's local skill library
- A skill bundle has been downloaded and needs to be unpacked into the correct location
- An agent team is being set up and its required skills need to be installed

Do NOT use when:
- The goal is to create a new skill (use `skill-authoring`)
- The goal is to package a skill for distribution (use `skill-packaging`)
- The skill is already installed — verify with a listing before re-installing

# Operating procedure
1. **Identify the source**: Is the skill coming from a local path, a zip bundle, a registry URL, or a GitHub repo? Confirm the source is accessible
2. **Identify the target location**: Determine the correct installation path for the target client:
   - GitHub Copilot: `.github/copilot/skills/SKILLNAME/`
   - OpenCode: `.opencode/skills/SKILLNAME/`
   - Gemini CLI: check client-specific conventions
   - Generic: ask user or consult AGENTS.md for the project's skill directory
3. **Verify the skill bundle integrity** (if installing from a zip or registry):
   - Unpack to a temp directory
   - Verify `manifest.json` exists and SKILL.md checksum matches
   - Confirm compatibility: does the `compatibility.clients` list include the target client?
4. **Copy skill files to the target location**: Create the skill directory, copy SKILL.md and any subdirectories (`tests/`, `references/`, `overlays/`, `examples/`)
5. **Register in skills-lock.json** (if the project uses one): Add the skill entry with name, version, source, and install path
6. **Verify installation**: Confirm SKILL.md is readable at the installed path. If the client has a skill listing command, run it to confirm the skill appears
7. **Test trigger** (optional but recommended): Run one of the skill's trigger prompts from `tests/triggers.md` if available and confirm the skill fires

# Output defaults
A confirmation that the skill was installed at the correct path, the skills-lock.json entry (if applicable), and a brief **Installation Verification** showing the file is present and correctly structured.

# Failure handling
If the target location is ambiguous or the client's skill convention is unknown, list what needs to be determined (client type, directory convention) before installation can proceed.
