---
name: fastapi-patterns
description: A FastAPI patterns skill covering route definition, dependency injection, Pydantic models, and async patterns. Use when building Python APIs with FastAPI.
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
  tags: [fastapi, python, api, backend]
---

# Purpose
A FastAPI patterns skill covering route definition, dependency injection, Pydantic models, and async patterns.

# When to use this skill
Use when:
- Building API endpoints with FastAPI
- Structuring FastAPI apps with routers and dependencies
- Validating request/response schemas with Pydantic

Do NOT use when:
- Non-FastAPI Python web frameworks (Flask, Django)
- Non-Python API backends

# Operating procedure
1. Define Pydantic models for request and response
2. Use FastAPI router for route grouping
3. Implement dependency injection for shared logic
4. Add async patterns for I/O-bound operations
5. Test with TestClient and validate OpenAPI schema

# Output defaults
FastAPI route handlers, Pydantic schemas, router configs, dependency definitions

# Failure handling
If validation errors occur, check Pydantic model field types. Use response_model for output.
