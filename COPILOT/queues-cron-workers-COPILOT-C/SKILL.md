---
name: queues-cron-workers
description: Structures scheduled jobs, background workers, retry logic, and queue observability for production systems. Use when implementing async task processing or periodic jobs.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cloud-platform-devops
  priority: P2
  maturity: draft
  risk: low
  tags: [queues, cron, workers, background-jobs]
---

# Purpose
Structures scheduled jobs, background workers, retry logic, and queue observability for production systems.

# When to use this skill
Use when:
- Implementing background job processing with queues
- Setting up cron schedules for periodic tasks
- Adding retry logic and dead-letter queues

Do NOT use when:
- Real-time synchronous API requests
- Simple single-process scripts without async needs

# Operating procedure
1. Choose queue technology appropriate to scale (SQS, BullMQ, Celery)
2. Define job schema with idempotency keys
3. Implement retry with exponential backoff
4. Set up dead-letter queue and alerts
5. Monitor queue depth and job latency

# Output defaults
Queue configs, worker scripts, cron job definitions, monitoring dashboards

# Failure handling
If jobs pile up, scale workers first. Investigate root cause before raising timeouts.
