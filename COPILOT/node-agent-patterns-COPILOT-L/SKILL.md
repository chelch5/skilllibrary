---
name: node-agent-patterns
description: "Encodes rules for lightweight per-machine agents, bounded subprocess work, and safe transport. Directly relevant to your MCP hub/node design. Trigger when the task context clearly involves node agent patterns."
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
  tags: [agents, node, subprocess]
---

# Purpose
Apply proven Node.js patterns for building agent implementations — lightweight per-machine nodes, bounded subprocess work, safe transport handling, and MCP-compatible tool exposure.

# When to use this skill
Use when:
- Building a Node.js agent that needs to run as a subprocess or background process
- Implementing MCP tools in Node.js
- Designing agent communication transport (stdio, HTTP, WebSocket)
- A Node.js agent is leaking resources, hanging on exit, or producing garbled output

Do NOT use when:
- The agent is implemented in a different language
- The task is general Node.js development unrelated to agent patterns

# Operating procedure
1. **Transport selection**:
   - Use `stdio` for single-machine, single-session agents (simplest, no network attack surface)
   - Use `HTTP/SSE` for multi-client or remote agents
   - Never use raw WebSocket without a reconnect/backoff wrapper
2. **Process lifecycle**:
   - Always handle `SIGTERM` and `SIGINT` with graceful shutdown (drain in-flight requests, then exit 0)
   - Use `process.exitCode = 1` instead of `process.exit(1)` to allow async cleanup
   - Never call `process.exit()` from inside a tool handler — throw instead and let the framework handle it
3. **Tool implementation pattern**:
   ```js
   // Good: bounded, named, typed
   server.tool('get-file', { path: z.string() }, async ({ path }) => {
     const content = await fs.readFile(resolveSafe(path), 'utf8');
     return { content: [{ type: 'text', text: content }] };
   });
   ```
4. **Resource bounds**: every tool must have a timeout (default 30s), a max output size (default 1MB), and explicit error handling
5. **Error surface**: return `isError: true` in the tool result for user-visible errors; throw only for unrecoverable agent errors
6. **Testing**: use `@modelcontextprotocol/sdk/testing` for in-process agent testing; never require a live network for unit tests

# Output defaults
Implemented tool handlers + graceful shutdown logic. Tests for each tool.

# Failure handling
If a tool times out, return a structured timeout error with the elapsed time. Do not let hanging tools block the agent process.
