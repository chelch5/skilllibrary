---
name: background-jobs-queues
description: Handles deferred work, retries, idempotency, scheduling, and worker boundaries. Use when offloading work from the request path. Do NOT use for realtime event streaming.
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
  tags: [jobs, queues, workers, async, retry, idempotency]
---

# Purpose
Establishes safe patterns for background processing: job queues, worker pools, retry strategies, and idempotency guards.

# When to use this skill
Use when:
- Moving slow or unreliable work off the HTTP request path
- Designing retry-safe job handlers
- Setting up a scheduled task or cron-style pipeline

Do NOT use when:
- Building realtime event fans (use realtime-websocket)
- Processing must be synchronous and inline

# Operating procedure
1. Choose queue backend (Redis, SQS, DB-backed, etc.)
2. Define job schema with idempotency key
3. Implement producer: enqueue with deduplication
4. Implement worker: claim, process, ack/nack
5. Add dead-letter queue and alerting
6. Test failure and retry paths explicitly

# Output defaults
Job schema definition + worker skeleton + retry/DLQ configuration.

# Failure handling
On poison messages, move to DLQ after max retries. Log full job payload at failure. Never silently drop a job.
