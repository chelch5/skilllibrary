---
name: mcp-inspector-debugging
description: Uses inspector tooling, schema checks, logs, and host traces to debug MCP failures. Trigger when an MCP tool call fails or produces unexpected results. Do NOT use for proactive security hardening.
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
  tags: [mcp, debugging, inspector]
---

# Purpose
Provides a systematic debugging approach for MCP failures using inspector tools, schema validation, request/response logs, and host-side traces.

# When to use this skill
Use when:
- An MCP tool call returns an unexpected error or result
- A host reports that an MCP tool is unavailable or returns bad data

Do NOT use when:
- Doing proactive security audits (use mcp-security-permissions)
- Writing tests (use mcp-testing-evals)

# Operating procedure
1. Capture the full request/response for the failing tool call
2. Validate the request against the tool's input schema
3. Check server logs for handler errors, panics, or unexpected state
4. Use MCP Inspector or equivalent to replay the call in isolation
5. Identify the failure layer (schema, handler, transport, auth) and fix it

# Output defaults
A debug report with failure classification, reproduction steps, root cause, and fix applied.

# Failure handling
If the failure is non-deterministic and cannot be reproduced, add logging to capture the next occurrence and flag for monitoring.
