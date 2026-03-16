---
name: mcp-protocol
description: "Applies repo-specific MCP protocol, schema, and fail-closed policies. For MCP repos this should probably be upgraded into a deeper pack. Trigger when the task context clearly involves mcp protocol."
source: github.com/gpttalker/opencode-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P1
  maturity: draft
  risk: low
  tags: [mcp, protocol, schema]
---

# Purpose
Apply MCP protocol fundamentals correctly — tools, resources, prompts, transports, and auth — for both MCP server and client implementations.

# When to use this skill
Use when:
- Implementing an MCP server (tool provider) or MCP client (tool consumer)
- Debugging MCP communication failures (malformed messages, wrong capabilities)
- Adding a new tool, resource, or prompt to an existing MCP server
- Choosing between MCP transports for a new deployment

Do NOT use when:
- The task involves general API design unrelated to MCP (use api-schema instead)
- The MCP server is already working and only business logic needs changing

# Operating procedure
1. **Understand the primitives**:
   - `tools` — functions the model can call; must be deterministic, bounded, return typed results
   - `resources` — read-only data sources (files, DB records) the model can inspect
   - `prompts` — parameterized prompt templates the model or user can invoke
   - `sampling` — server-initiated model calls (advanced; requires explicit client capability declaration)
2. **Transport rules**:
   - `stdio`: parent process spawns server; use for local tools; message framing is newline-delimited JSON
   - `HTTP+SSE`: server at `/sse` for server→client stream, `POST /messages` for client→server; use for remote/multi-client
   - `Streamable HTTP` (MCP 2025-03-26+): single endpoint, bidirectional; prefer for new remote deployments
3. **Capability negotiation**: server must declare capabilities in `initialize` response; client must not call undeclared capabilities
4. **Tool schema rules**: use JSON Schema draft 7; all parameters must have `description`; mark required fields explicitly
5. **Auth (OAuth 2.1)**: for remote servers, implement PKCE flow; never pass tokens in tool parameters; use `Authorization: Bearer` header
6. **Error codes**: use MCP error codes (`-32600` invalid request, `-32601` method not found, `-32603` internal) not HTTP codes in JSON-RPC responses
7. **Versioning**: always echo the negotiated protocol version; do not assume latest

# Output defaults
Working tool/resource/prompt handlers + capability declaration. Protocol version pinned in server config.

# Failure handling
If the client sends a capability the server did not declare, return `-32601` (method not found) — do not implement the capability ad hoc.
