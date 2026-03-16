---
name: mcp-development
description: Covers end-to-end MCP server design, tool surfaces, resources, prompts, and repo conventions. Trigger when building or reviewing any MCP server from scratch. Do NOT use for isolated tool design or transport-only questions.
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
  tags: [mcp, server, development]
---

# Purpose
Provides end-to-end guidance for designing, building, and structuring an MCP server including tools, resources, prompts, and repo conventions.

# When to use this skill
Use when:
- Building a new MCP server from the ground up
- Reviewing an existing MCP server for architectural completeness

Do NOT use when:
- Only designing a single isolated tool (use mcp-tool-design)
- Only configuring transport or auth (use mcp-auth-transports)

# Operating procedure
1. Define the server's purpose and the tool surfaces it will expose
2. Structure the repo with clear separation of tool handlers, resources, and prompts
3. Implement tool registration with proper schema validation
4. Add resource and prompt definitions alongside tool definitions
5. Write integration tests and a local dev startup procedure

# Output defaults
A complete MCP server skeleton with tool, resource, and prompt definitions, plus a README with startup and usage instructions.

# Failure handling
If a tool handler produces schema-invalid responses, catch and return a structured error response. Never surface raw stack traces to the host.
