---
name: api-debugging
description: Focused debugging pack for request/response mismatches, schema issues, and transport problems. Use when an API call fails unexpectedly. Do NOT use for designing contracts or building new endpoints.
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
  tags: [api, debugging, http, troubleshooting]
---

# Purpose
Systematically diagnoses API failures by isolating transport, auth, schema, and logic layers.

# When to use this skill
Use when:
- A request returns an unexpected status code or malformed body
- Client and server disagree on schema or encoding
- Intermittent failures need reproduction steps

Do NOT use when:
- Designing new API contracts (use api-contracts)
- Investigating database query issues (use postgresql or sqlite)

# Operating procedure
1. Capture raw request and response (headers, body, status)
2. Verify transport layer: TLS, DNS, proxies
3. Check authentication: token format, expiry, scope
4. Validate request body against schema
5. Trace through middleware stack for early exits
6. Reproduce with minimal curl / httpie command

# Output defaults
Minimal reproduction command + root cause annotation + fix recommendation.

# Failure handling
If the request cannot be reproduced locally, add logging at the boundary, redeploy, and capture a real trace before diagnosing further.
