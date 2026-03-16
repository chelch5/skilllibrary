---
name: mcp-python-fastmcp
description: Applies Python FastMCP-style conventions for building MCP servers with minimal boilerplate. Trigger when building an MCP server in Python using FastMCP. Do NOT use for TypeScript or Go MCP server work.
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
  tags: [mcp, python, fastmcp]
---

# Purpose
Provides FastMCP-specific patterns for building Python-based MCP servers with decorator-driven tool registration and minimal boilerplate.

# When to use this skill
Use when:
- Building an MCP server in Python using the FastMCP library
- Refactoring a raw Python MCP server to use FastMCP conventions

Do NOT use when:
- Using TypeScript SDK (use mcp-typescript-sdk) or Go (use mcp-go-server)
- General Python backend work unrelated to MCP

# Operating procedure
1. Install FastMCP and set up the server entry point
2. Register tools using `@mcp.tool()` decorators with Pydantic input models
3. Define resource endpoints using `@mcp.resource()` decorators
4. Run the server with the appropriate transport (stdio or HTTP)
5. Write tests using FastMCP's testing utilities

# Output defaults
A Python FastMCP server with decorated tool and resource definitions, Pydantic schemas, and a working transport configuration.

# Failure handling
If a tool raises an unhandled exception, FastMCP should catch it and return a structured error. Add custom error handling for domain-specific failure cases.
