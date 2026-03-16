---
name: mcp-resources-prompts
description: Covers non-tool MCP surfaces including resources, prompt templates, and discovery metadata. Trigger when designing MCP resources or prompt definitions. Do NOT use for tool surface design.
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
  tags: [mcp, resources, prompts]
---

# Purpose
Guides the design and implementation of MCP resources (data surfaces) and prompt templates, which extend the MCP surface beyond tool calls.

# When to use this skill
Use when:
- Adding MCP resource endpoints that expose structured data to hosts
- Designing reusable prompt templates that hosts can invoke

Do NOT use when:
- Designing tool call surfaces (use mcp-tool-design)
- Debugging tool failures (use mcp-inspector-debugging)

# Operating procedure
1. Define resource URIs with a clear naming scheme and content type
2. Implement resource handlers that return structured, schema-validated content
3. Design prompt templates with variable slots and usage documentation
4. Register resources and prompts in the server's discovery metadata
5. Test that hosts can enumerate and invoke all registered resources and prompts

# Output defaults
Resource definitions with URI, content type, and handler; prompt template definitions with slots and examples.

# Failure handling
If a resource is unavailable at request time, return a structured not-found response with a descriptive message.
