---
name: tool-use-agents
description: Provides patterns for agents that use tools effectively, including tool selection, chaining, error recovery, and avoiding tool overuse. Trigger when designing or debugging an agent's tool-use behavior. Do NOT use for designing the tools themselves.
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
  tags: [tools, agents, patterns]
---

# Purpose
Defines patterns for agents that use tools effectively: when to call tools, how to chain them, how to recover from failures, and how to avoid excessive tool calling.

# When to use this skill
Use when:
- Designing how an agent should select and sequence tool calls
- Debugging an agent that is calling tools incorrectly, excessively, or in the wrong order

Do NOT use when:
- Designing the tool implementations themselves (use mcp-tool-design)
- Orchestrating multiple agents (use agent-orchestration)

# Operating procedure
1. Define the decision rule for when to call a tool vs. answer from context
2. Design tool call chains with clear inputs and outputs between steps
3. Implement error recovery: retry transient errors, fail fast on permanent errors
4. Set a maximum tool call budget per task to prevent runaway loops
5. Log all tool calls for debugging and optimization

# Output defaults
A tool-use policy document with selection rules, chaining patterns, error recovery procedures, and call budget limits.

# Failure handling
If a tool call fails after retries, surface the failure clearly to the orchestrator rather than guessing or inventing a response.
