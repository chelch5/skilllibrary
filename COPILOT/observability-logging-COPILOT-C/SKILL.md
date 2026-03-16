---
name: observability-logging
description: Covers structured logs, traces, metrics, correlation IDs, and safe diagnostic output. Use when adding observability to a service. Do NOT use for application business logic.
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
  tags: [observability, logging, tracing, metrics, structured-logs]
---

# Purpose
Establishes structured, queryable logging and tracing conventions that aid debugging without leaking sensitive data.

# When to use this skill
Use when:
- Adding logging or tracing to a new service
- Reviewing log output for PII leakage or missing correlation
- Setting up metrics endpoints or health checks

Do NOT use when:
- Debugging a specific live incident (use api-debugging)
- Business logic implementation

# Operating procedure
1. Use structured logger (zap, logrus, structlog) with JSON output
2. Inject correlation/trace ID at service entry point
3. Log at INFO for normal flow, ERROR for unexpected failures only
4. Never log PII, tokens, or passwords even at DEBUG
5. Add /health and /metrics endpoints
6. Propagate trace context via headers (W3C TraceContext)

# Output defaults
Logger setup snippet + middleware for correlation ID + health endpoint template.

# Failure handling
If log volume exceeds storage budget, raise log level to WARN. If trace context is missing from upstream, generate a new ID and flag the gap.
