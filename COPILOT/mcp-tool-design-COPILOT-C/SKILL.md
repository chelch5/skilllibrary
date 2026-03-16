---
name: mcp-tool-design
description: Designs MCP tools with safe contracts, good naming, narrow scope, and host-friendly schemas. Trigger when designing individual MCP tools or reviewing tool definitions. Do NOT use for full server architecture.
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
  tags: [mcp, tools, design]
---

# Purpose
Guides the design of individual MCP tools to ensure they have safe contracts, narrow scope, clear naming, and host-friendly JSON schemas.

# When to use this skill
Use when:
- Designing a new MCP tool or reviewing an existing tool definition
- Auditing tool naming, scope, and schema quality

Do NOT use when:
- Designing the full MCP server architecture (use mcp-development)
- Writing transport or auth code

# Operating procedure
1. Define the tool's single responsibility and the exact action it performs
2. Name the tool with a clear verb-noun pattern (e.g., get-file, list-repos)
3. Design the input schema with required vs optional fields and clear descriptions
4. Design the output schema to be structured and host-parseable
5. Add safety constraints: what the tool cannot do, what inputs it rejects

# Output defaults
A tool definition with name, description, input schema, output schema, and safety constraints in the MCP tool spec format.

# Failure handling
If tool execution fails, return a structured error with a code and message. Do not throw unhandled exceptions.
