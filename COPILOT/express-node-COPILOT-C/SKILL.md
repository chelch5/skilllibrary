---
name: express-node
description: Applies Express/Node service structure, middleware, validation, and routing conventions. Use when building or reviewing a Node.js HTTP service. Do NOT use for frontend React work.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P2
  maturity: draft
  risk: low
  tags: [express, node, javascript, backend, routing]
---

# Purpose
Establishes consistent Express application structure with validation, error handling, and middleware ordering.

# When to use this skill
Use when:
- Scaffolding a new Express API service
- Reviewing middleware order or error propagation
- Adding input validation or auth middleware

Do NOT use when:
- Building frontend React/Next.js apps
- Working with a different backend framework (FastAPI, Flask)

# Operating procedure
1. Organise routes into feature modules (routes/, controllers/, services/)
2. Add request validation middleware (zod or joi) before route handlers
3. Centralise error handling with a final error-handling middleware
4. Use async handler wrappers to catch rejected promises
5. Configure logging with correlation IDs at the middleware layer
6. Never expose stack traces in production error responses

# Output defaults
Route module skeleton + middleware stack order + error handler template.

# Failure handling
Unhandled promise rejections must be caught by wrapper or process event. Log and respond with 500; never let Express silently swallow errors.
