---
name: mcp-typescript-sdk
description: Applies TypeScript SDK patterns for MCP server development, tool registration, and runtime type boundaries. Trigger when building an MCP server in TypeScript. Do NOT use for Python or Go MCP server work.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: mcp
  priority: P1
  maturity: draft
  risk: low
  tags: [mcp, typescript, sdk]
---

# Purpose
Provides TypeScript-specific patterns for building MCP servers using the official TypeScript SDK, with emphasis on type safety and idiomatic patterns.

# When to use this skill
Use when:
- Building or refactoring an MCP server in TypeScript
- Applying TypeScript SDK conventions for tool registration and type safety

Do NOT use when:
- Building MCP servers in Python (use mcp-python-fastmcp) or Go (use mcp-go-server)
- General TypeScript questions unrelated to MCP

# Operating procedure
1. Install and configure the MCP TypeScript SDK
2. Define tool schemas using Zod or JSON Schema with full type inference
3. Register tools with typed handlers that enforce input and output types
4. Use the SDK's Server class for transport abstraction
5. Apply strict TypeScript compiler settings to catch schema-handler mismatches

# Output defaults
A TypeScript MCP server with fully typed tool definitions, Zod schemas, and a working stdio or HTTP transport setup.

# Failure handling
If TypeScript types diverge from runtime behavior, add runtime validation at the handler boundary as a safety net.
