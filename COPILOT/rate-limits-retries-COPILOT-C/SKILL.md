---
name: rate-limits-retries
description: Explains client and server-side rate control, exponential backoff, and failure classification. Use when consuming or hosting APIs with rate limits. Do NOT use for queue-based async processing.
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
  tags: [rate-limiting, retries, backoff, resilience, throttling]
---

# Purpose
Provides reliable patterns for honouring rate limits on consumed APIs and enforcing them on hosted services.

# When to use this skill
Use when:
- Calling a third-party API with known rate limits (OpenAI, GitHub, etc.)
- Adding server-side rate limiting to a public endpoint
- Designing retry logic for transient failures

Do NOT use when:
- Background queue processing (use background-jobs-queues)
- Circuit-breaker patterns for service meshes

# Operating procedure
1. Classify errors: retryable (429, 503, network) vs terminal (400, 401, 403)
2. Implement exponential backoff with jitter: base * 2^attempt + rand(0, base)
3. Respect Retry-After header when present
4. Add max retry budget (count + total timeout)
5. On server side: use token bucket or sliding window algorithm
6. Track 429 rate in metrics; alert when sustained

# Output defaults
Retry decorator/middleware + rate limit enforcement example + backoff formula.

# Failure handling
After max retries, raise a terminal error with full context. Log retry attempts at DEBUG, final failure at ERROR.
