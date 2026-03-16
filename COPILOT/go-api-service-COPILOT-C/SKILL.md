---
name: go-api-service
description: Applies Go service layout, handler structure, context usage, and validation boundaries to API backends. Use when building Go HTTP services. Do NOT use for CLI tool development.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P1
  maturity: draft
  risk: low
  tags: [go, api, http, service, handlers]
---

# Purpose
Provides a clean Go HTTP service structure with idiomatic handler, middleware, and context propagation patterns.

# When to use this skill
Use when:
- Building a new Go REST or RPC service
- Reviewing handler organisation and context threading
- Adding middleware (auth, logging, timeout)

Do NOT use when:
- Building a CLI tool (use cli-development-go or cobra-go)
- Working with gRPC exclusively

# Operating procedure
1. Define service struct embedding dependencies (DB, logger, config)
2. Register handlers as methods on the service struct
3. Thread context.Context from handler to all downstream calls
4. Validate inputs at handler boundary before passing to service layer
5. Use http.StatusXxx constants; never hardcode numbers
6. Wrap errors with %w for unwrapping; log at handler level only

# Output defaults
Service struct + handler template + middleware chain example.

# Failure handling
Return structured JSON errors. Propagate context cancellation; clean up resources in defer. Log unexpected errors with full request context before responding 500.
