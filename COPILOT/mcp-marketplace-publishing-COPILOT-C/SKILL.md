---
name: mcp-marketplace-publishing
description: Packages MCP servers or skill bundles for publication, distribution, or catalog inclusion. Trigger when preparing an MCP server for public release or catalog submission. Do NOT use for internal-only server deployments.
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
  tags: [mcp, publishing, marketplace]
---

# Purpose
Guides the packaging and publication of MCP servers or skill bundles for marketplace inclusion, public distribution, or catalog discovery.

# When to use this skill
Use when:
- Preparing an MCP server for submission to an AI tool marketplace or catalog
- Creating a distributable package from an MCP server

Do NOT use when:
- Deploying an MCP server for internal use only
- General deployment configuration (use mcp-host-integration)

# Operating procedure
1. Write a complete manifest with name, description, version, and tool list
2. Add a clear README with installation steps, required config, and usage examples
3. Package the server with its dependencies in a reproducible way (npm publish, Docker image, etc.)
4. Add a license file and a SECURITY policy
5. Submit to the target marketplace or catalog following their submission guidelines

# Output defaults
A publishable package with manifest, README, license, and distribution artifact.

# Failure handling
If the marketplace validation rejects the submission, review the validation report item by item and fix all reported issues before resubmitting.
