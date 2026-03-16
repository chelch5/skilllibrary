---
name: mcp-go-server
description: Applies Go idioms and service structure to an MCP server implementation. Trigger when building an MCP server in Go. Do NOT use for TypeScript or Python MCP server work.
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
  tags: [mcp, go, server]
---

# Purpose
Provides Go-idiomatic patterns for building MCP servers, including tool registration, JSON schema generation, and stdio/HTTP transport setup.

# When to use this skill
Use when:
- Building an MCP server in Go
- Applying Go idioms (interfaces, error handling, goroutines) to an MCP server

Do NOT use when:
- Using TypeScript (use mcp-typescript-sdk) or Python (use mcp-python-fastmcp)
- General Go development unrelated to MCP

# Operating procedure
1. Set up the Go module and import the MCP Go SDK or equivalent
2. Define tool handlers as Go functions with typed input/output structs
3. Generate JSON schemas from Go types using struct tags or reflection
4. Register tools and start the server with stdio or HTTP transport
5. Write table-driven unit tests for tool handlers

# Output defaults
A Go MCP server with typed handlers, JSON schema generation, and a working transport setup.

# Failure handling
Use Go's idiomatic error return pattern. Wrap errors with context before returning them as MCP error responses.
