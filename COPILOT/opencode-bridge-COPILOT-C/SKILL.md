---
name: opencode-bridge
description: Explains how project-local skills and operating surfaces bind into OpenCode-specific conventions. Trigger when adapting a general skill or tool for use in the OpenCode environment. Do NOT use for non-OpenCode agent platforms.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P2
  maturity: draft
  risk: low
  tags: [opencode, bridge, integration]
---

# Purpose
Bridges general skill designs to OpenCode's specific conventions, ensuring project-local skills integrate cleanly with `.opencode/` structures.

# When to use this skill
Use when:
- Adapting a newly created skill to work within OpenCode
- Configuring Scafforge-generated skills for OpenCode deployment

Do NOT use when:
- Targeting a different agent platform (use a platform-specific bridge)
- Writing a skill from scratch without an existing general design

# Operating procedure
1. Review the general skill design and identify integration points
2. Map each integration point to the corresponding OpenCode primitive (path, config, registration)
3. Update file paths, naming, and configuration to match OpenCode conventions
4. Validate the adapted skill in an OpenCode environment

# Output defaults
An adapted skill with updated OpenCode-compatible paths, naming, and configuration.

# Failure handling
If OpenCode conventions conflict with the skill's requirements, document the conflict and propose a resolution before proceeding.
