---
name: mcp-testing-evals
description: Tests MCP tools, transports, permission behavior, and end-to-end host interactions under repeatable scenarios. Trigger when writing tests for an MCP server. Do NOT use for general backend testing unrelated to MCP.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: mcp
  priority: P0
  maturity: draft
  risk: low
  tags: [mcp, testing, evals]
---

# Purpose
Provides testing and evaluation patterns for MCP servers covering tool contracts, transport behavior, security permissions, and end-to-end host interactions.

# When to use this skill
Use when:
- Writing tests for a new or existing MCP server
- Setting up a CI pipeline that validates MCP tool contracts

Do NOT use when:
- Testing general backend application code unrelated to MCP
- Evaluating LLM output quality (use benchmark-design)

# Operating procedure
1. Write unit tests for each tool handler's input validation and output schema
2. Write transport tests verifying that tools are reachable via the configured transport
3. Write permission tests: verify that gated tools reject unauthorized callers
4. Write end-to-end tests simulating a host (Claude, ChatGPT) calling the server
5. Add regression tests for any previously discovered bugs

# Output defaults
A test suite with unit, transport, permission, and end-to-end tests plus a CI configuration snippet.

# Failure handling
If a test fails in CI, block the merge. Include enough context in the failure message to diagnose without local reproduction.
