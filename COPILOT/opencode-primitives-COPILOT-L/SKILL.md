---
name: opencode-primitives
description: Holds exact OpenCode path, naming, and configuration primitives that other skills can reference. Trigger when setting up or referencing OpenCode-specific structures. Do NOT use as a general MCP or tool configuration guide.
source: github.com/sst/opencode
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P2
  maturity: draft
  risk: low
  tags: [opencode, primitives, configuration]
---

# Purpose
Provides a compact reference for OpenCode-specific path, naming, and configuration primitives that skill authors and agents can rely on.

# When to use this skill
Use when:
- Writing or configuring skills, agents, or tools that target the OpenCode environment
- Verifying correct OpenCode directory structure and naming conventions

Do NOT use when:
- Writing general MCP server code unrelated to OpenCode conventions
- Looking for general tool configuration guidance

# Operating procedure
1. Reference OpenCode's `.opencode/` directory structure
2. Verify skill and agent file naming conventions
3. Check configuration schema for agents, tools, and skill registration
4. Use these primitives as the baseline for any OpenCode-targeted skill or agent

# Output defaults
A reference card with OpenCode directory layout, naming conventions, and configuration schema snippets.

# Failure handling
If the OpenCode version has changed and primitives are outdated, flag the discrepancy and defer to the official OpenCode documentation.
