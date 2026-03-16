---
name: claude-api
description: A skill for integrating with the Claude API covering authentication, prompt structuring, tool use, and response handling. Use when building applications on the Anthropic Claude API.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: external-reference-seeds
  priority: P2
  maturity: draft
  risk: low
  tags: [claude, anthropic, api, llm]
---

# Purpose
A skill for integrating with the Claude API covering authentication, prompt structuring, tool use, and response handling.

# When to use this skill
Use when:
- Integrating Claude API into an application
- Structuring prompts and tool definitions for Claude
- Handling Claude API responses and error cases

Do NOT use when:
- Other LLM APIs with different schemas (use appropriate provider skill)
- Self-hosted model deployment

# Operating procedure
1. Set up API authentication with API key
2. Structure messages array with system and user roles
3. Define tools with JSON schema if using tool use
4. Handle response types (text, tool_use, stop_reason)
5. Implement retry logic for rate limits and errors

# Output defaults
Claude API integration code, message structures, tool definitions, error handling

# Failure handling
If rate limited, implement exponential backoff. Log stop_reason for debugging.
