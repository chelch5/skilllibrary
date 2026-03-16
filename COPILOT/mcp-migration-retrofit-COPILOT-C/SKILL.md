---
name: mcp-migration-retrofit
description: Retrofits an existing application or tool into an MCP-compatible surface without a blind rewrite. Trigger when exposing existing functionality as MCP tools. Do NOT use for greenfield MCP server builds.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: mcp
  priority: P2
  maturity: draft
  risk: low
  tags: [mcp, migration, retrofit]
---

# Purpose
Guides the incremental retrofit of existing applications or tools into MCP-compatible surfaces without requiring a full rewrite.

# When to use this skill
Use when:
- Wrapping an existing CLI, API, or service as MCP tools
- Incrementally adding MCP compatibility to a running system

Do NOT use when:
- Building a new MCP server from scratch (use mcp-development)
- Full rewriting the system under the guise of "migration"

# Operating procedure
1. Inventory existing functionality and identify the most valuable subset to expose as MCP tools
2. Design a thin adapter layer between the existing code and MCP tool handlers
3. Implement the adapter without modifying the existing codebase internals
4. Register the adapted tools in an MCP server wrapper
5. Test that the adapter produces correct MCP responses from existing behavior

# Output defaults
An adapter layer with MCP tool definitions wrapping existing functionality, plus integration tests.

# Failure handling
If the existing system's behavior is non-deterministic or poorly documented, add defensive validation in the adapter layer before exposing it as an MCP tool.
