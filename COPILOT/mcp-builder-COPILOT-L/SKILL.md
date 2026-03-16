---
name: mcp-builder
description: Build, structure, and evaluate an MCP server end-to-end, covering tool surfaces, resource and prompt definitions, schema contracts, transport setup, and the four-phase workflow (research → implement → review/test → evals). Trigger when the task involves constructing a new MCP server or a major revision to an existing one. Do NOT use for isolated single-tool changes (use mcp-tool-design) or transport-only work (use mcp-auth-transports).
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: mcp
  priority: P1
  maturity: stable
  risk: low
  tags: [mcp, server, tools, resources, prompts, eval]
---

# Purpose
Guides the full lifecycle of building a production-quality MCP server: from capability research through tool design, implementation, review, and evaluation.

# When to use this skill
Use when:
- Building a new MCP server from scratch
- Adding a major new capability surface (tools + resources + prompts) to an existing server
- Conducting a structured review of an MCP server's design and test coverage

Do NOT use when:
- Adding a single isolated tool to an existing server (use `mcp-tool-design`)
- Only configuring transport or authentication (use `mcp-auth-transports`)
- Only writing schema contracts (use `mcp-schema-contracts`)

# Operating procedure

**Phase 1 — Research**
1. Define the server's purpose and the problems it solves for host applications
2. Enumerate the tool surfaces: what operations will be exposed?
3. Identify required resources (static data) and prompt templates
4. Check the MCP spec for tool naming conventions and annotation requirements

**Phase 2 — Implement**
1. Register each tool with a precise name (`verb_noun` convention), description, and input schema
2. Implement tool handlers with strict input validation before any side effect
3. Add resource definitions with URI templates for any readable data
4. Add prompt definitions for common interaction patterns
5. Apply `readOnlyHint`, `destructiveHint`, `idempotentHint` annotations accurately

**Phase 3 — Review and test**
1. Review each tool description: would an LLM pick the right tool from the description alone?
2. Test each tool with valid inputs, missing inputs, and out-of-range inputs
3. Confirm all error responses use structured MCP error objects, not raw exceptions
4. Confirm no tool leaks internal stack traces or credentials

**Phase 4 — Evals**
1. Write at least two trigger test prompts per tool (one that should invoke it, one that should not)
2. Compare tool output with and without the server to verify it adds value
3. Document expected output shape and latency budget

# Output defaults
Working MCP server with tool/resource/prompt registration, input schemas, handler implementations, and a README with local dev startup instructions.

# Failure handling
If a tool handler throws, return a structured MCP error response — never a raw exception. If a resource URI cannot be resolved, return a descriptive 404-equivalent error object.
