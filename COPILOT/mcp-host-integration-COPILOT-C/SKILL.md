---
name: mcp-host-integration
description: Handles how an MCP server fits into ChatGPT, Claude, OpenCode, Codex, or other hosts and their differing expectations. Trigger when connecting an MCP server to a specific AI host. Do NOT use for general server design.
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
  tags: [mcp, host, integration]
---

# Purpose
Guides the integration of an MCP server with specific AI hosts, accounting for each host's connection protocol, capability discovery, and tool-call conventions.

# When to use this skill
Use when:
- Connecting an existing MCP server to a new host (ChatGPT, Claude, OpenCode, Codex)
- Debugging host-specific incompatibilities in an MCP server

Do NOT use when:
- Designing the server's internal tool or resource surfaces
- Setting up transport and auth (use mcp-auth-transports)

# Operating procedure
1. Review the target host's MCP client documentation and capability expectations
2. Verify the server's capability manifest matches what the host expects
3. Test tool discovery: the host should enumerate all tools correctly
4. Test a sample tool call end-to-end and verify the host parses the response
5. Document any host-specific quirks and workarounds

# Output defaults
A host integration guide with connection config, discovery verification steps, and host-specific notes.

# Failure handling
If the host cannot discover the server's tools, check the server's capability manifest first before investigating transport or auth issues.
