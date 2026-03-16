---
name: mcp-multi-tenant-design
description: Designs isolation, auth, state partitioning, and limits when one MCP service serves multiple tenants. Trigger when designing a shared MCP server with multiple users or organizations. Do NOT use for single-user local MCP servers.
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
  tags: [mcp, multi-tenant, isolation]
---

# Purpose
Provides design patterns for MCP servers that serve multiple tenants, covering isolation, authentication, state partitioning, and rate limiting.

# When to use this skill
Use when:
- Building a hosted MCP server that multiple organizations or users will share
- Adding tenant isolation to an existing single-tenant MCP server

Do NOT use when:
- Building a local single-user MCP server
- General auth design (use mcp-auth-transports)

# Operating procedure
1. Define the tenant model (per-org, per-user, per-API-key)
2. Implement tenant context injection at the transport/auth layer
3. Partition all state (data, config, logs) by tenant identifier
4. Apply per-tenant rate limits and quotas
5. Audit all tool handlers for accidental cross-tenant data leaks

# Output defaults
A multi-tenant design document with tenant model, isolation strategy, state partitioning design, and quota configuration.

# Failure handling
If a tenant context cannot be determined from a request, reject the request with a clear error. Never fall back to a shared or default tenant.
