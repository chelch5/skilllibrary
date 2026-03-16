---
name: api-contracts
description: Strengthens explicit API contracts, validation expectations, and compatibility behavior. Use when designing or reviewing API surfaces, schemas, or client–server agreements. Do NOT use for general debugging or runtime tracing.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P2
  maturity: draft
  risk: low
  tags: [api, contracts, validation, openapi, schema]
---

# Purpose
Enforces explicit, machine-verifiable API contracts so that producer and consumer stay in sync across versions and teams.

# When to use this skill
Use when:
- Designing a new API surface or versioning an existing one
- Reviewing schema drift or breaking-change risk in a PR
- Adding validation layers between services

Do NOT use when:
- Debugging a live API runtime error (use api-debugging instead)
- Modelling database schema (use data-model instead)

# Operating procedure
1. Identify the API surface: REST, GraphQL, gRPC, or event contract
2. Produce or update the canonical schema (OpenAPI, Proto, AsyncAPI)
3. Add request/response validation at the boundary layer
4. Annotate breaking vs non-breaking changes
5. Verify consumer compatibility tests exist

# Output defaults
Updated schema file + list of breaking changes with migration notes.

# Failure handling
If schema cannot be auto-generated, fall back to hand-authored OpenAPI with required fields marked. Flag unversioned endpoints as high-risk.
