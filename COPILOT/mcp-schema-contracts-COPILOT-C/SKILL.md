---
name: mcp-schema-contracts
description: Defines naming, schema evolution, validation, and backward-compatibility expectations for MCP surfaces. Trigger when versioning MCP tool or resource schemas. Do NOT use for initial tool design or transport decisions.
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
  tags: [mcp, schemas, contracts]
---

# Purpose
Establishes naming, evolution, and backward-compatibility rules for MCP tool, resource, and prompt schemas.

# When to use this skill
Use when:
- Updating an existing MCP schema and needing to ensure backward compatibility
- Establishing schema governance for a public or shared MCP server

Do NOT use when:
- Designing a brand-new tool for the first time (use mcp-tool-design)
- Debugging schema validation failures at runtime (use mcp-inspector-debugging)

# Operating procedure
1. Version all schemas explicitly in tool and resource definitions
2. Define additive-only change rules for backward compatibility (no field removals, no type changes)
3. Mark deprecated fields clearly and provide migration paths
4. Validate schemas against the MCP schema spec before publishing changes
5. Document breaking change procedures including migration periods

# Output defaults
A schema contract document with versioning policy, allowed change types, deprecation rules, and migration procedures.

# Failure handling
If a proposed change would break backward compatibility, block the change and propose an additive alternative.
