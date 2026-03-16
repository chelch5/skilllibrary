---
name: fastapi
description: Applies FastAPI route, dependency injection, validation, async, and schema conventions. Use when building Python HTTP APIs. Do NOT use for CPU-bound batch scripts.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P0
  maturity: draft
  risk: low
  tags: [fastapi, python, async, pydantic, api]
---

# Purpose
Structures FastAPI applications with clean dependency injection, typed Pydantic schemas, and async-safe patterns.

# When to use this skill
Use when:
- Building or reviewing a Python REST API with FastAPI
- Designing request/response Pydantic models
- Adding dependency injection for DB sessions or auth

Do NOT use when:
- Running CPU-intensive batch jobs (use background worker)
- Building non-HTTP services

# Operating procedure
1. Define Pydantic schemas for request and response separately
2. Use dependency injection (Depends) for shared resources (DB, auth)
3. Mark all I/O-bound route handlers as async
4. Add lifespan context manager for startup/shutdown
5. Return typed response models; never return raw dicts
6. Use HTTPException with appropriate status codes

# Output defaults
Router module with typed handlers + Pydantic models + dependency examples.

# Failure handling
Validation errors are automatically returned as 422. For business logic errors, raise HTTPException. Log unhandled exceptions before re-raising.
