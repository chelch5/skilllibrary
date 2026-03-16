---
name: mcp-security-permissions
description: Handles least privilege, tool gating, path restrictions, tenant boundaries, and fail-closed behavior for MCP systems. Trigger when hardening an MCP server's security posture. Do NOT use for auth/transport setup.
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
  tags: [mcp, security, permissions]
---

# Purpose
Applies security hardening to MCP servers through least privilege tool gating, path restrictions, tenant boundaries, and fail-closed defaults.

# When to use this skill
Use when:
- Hardening an MCP server before production deployment
- Auditing tool permissions and tenant isolation in an existing MCP server

Do NOT use when:
- Setting up auth/transport (use mcp-auth-transports)
- Designing tool schemas (use mcp-tool-design)

# Operating procedure
1. Enumerate all tools and assign them a permission tier (read-only, write, destructive)
2. Implement gating: require explicit caller permission for write and destructive tools
3. Restrict filesystem paths to explicitly allow-listed directories
4. Implement tenant isolation: no cross-tenant data access
5. Default to fail-closed: if a permission check fails or is uncertain, deny the action

# Output defaults
A security audit report with tool permission matrix, path restrictions applied, tenant isolation design, and fail-closed policy documentation.

# Failure handling
If a permission check cannot be resolved, deny the action and log the attempt with caller context.
