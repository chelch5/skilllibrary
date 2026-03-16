---
name: mcp-auth-transports
description: Handles stdio versus HTTP/SSE/WebSocket transport decisions and authentication layer design for MCP servers. Trigger when choosing or configuring MCP transport and auth. Do NOT use for tool design or schema questions.
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
  tags: [mcp, auth, transports]
---

# Purpose
Guides the selection of MCP transport (stdio, HTTP, SSE, WebSocket) and the design of any authentication layer on top.

# When to use this skill
Use when:
- Choosing a transport for a new MCP server deployment
- Adding authentication to an MCP server that previously had none

Do NOT use when:
- Designing tool surfaces or schemas (use mcp-tool-design)
- Setting up security permissions (use mcp-security-permissions)

# Operating procedure
1. Determine the deployment context (local CLI, remote server, embedded)
2. Select the appropriate transport: stdio for local/CLI, HTTP+SSE for remote
3. Design the auth layer: API key, OAuth, or bearer token based on host requirements
4. Implement transport-agnostic tool handlers that work with any transport layer
5. Test auth flows end-to-end before exposing publicly

# Output defaults
A transport and auth design document with transport selection rationale, auth scheme, and configuration examples.

# Failure handling
If auth fails, return a 401/403 response with a clear error message. Do not leak server details in error responses.
