---
name: mcp-chatgpt-app-bridge
description: Designs the bridge between a local or hosted MCP server and a ChatGPT app or tool surface. Trigger when integrating an MCP server specifically with ChatGPT. Do NOT use for Claude or OpenCode integration.
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
  tags: [mcp, chatgpt, bridge]
---

# Purpose
Guides the design and configuration of a bridge between an MCP server and ChatGPT's tool or app integration surfaces.

# When to use this skill
Use when:
- Making an existing MCP server accessible to ChatGPT
- Designing a custom ChatGPT app that calls an MCP server as its backend

Do NOT use when:
- Integrating with Claude (use mcp-host-integration with Claude context)
- Building for OpenCode (use opencode-bridge)

# Operating procedure
1. Review ChatGPT's current MCP or tool plugin integration model
2. Configure the MCP server's HTTP transport and auth to match ChatGPT's requirements
3. Write an OpenAPI or tool manifest that ChatGPT can discover
4. Test tool calls from a ChatGPT environment end-to-end
5. Handle ChatGPT-specific limitations (token limits, tool count limits, response formatting)

# Output defaults
A ChatGPT integration configuration with manifest, auth setup, and end-to-end test results.

# Failure handling
If ChatGPT cannot discover or call the tools, check the manifest format first. Validate against ChatGPT's published schema before investigating other causes.
