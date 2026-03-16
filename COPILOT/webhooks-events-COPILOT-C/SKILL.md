---
name: webhooks-events
description: Handles inbound event verification, idempotency, fanout, and asynchronous processing for webhook-driven systems. Use when receiving webhooks from external services. Do NOT use for internally generated events.
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
  tags: [webhooks, events, idempotency, verification, async]
---

# Purpose
Establishes secure, idempotent webhook ingestion with signature verification and reliable downstream processing.

# When to use this skill
Use when:
- Receiving webhooks from Stripe, GitHub, Twilio, or similar
- Designing an event ingestion endpoint
- Adding idempotency to event processing

Do NOT use when:
- Building internally generated domain events (use background-jobs-queues)
- Realtime bidirectional connections (use realtime-websocket)

# Operating procedure
1. Verify HMAC signature before processing any payload
2. Return 200 immediately; process asynchronously
3. Store event ID and check for duplicates before acting
4. Parse payload into typed struct; reject unknown event types
5. Fan out to handlers via internal queue or event bus
6. Implement dead-letter handling for failed processing

# Output defaults
Signature verification middleware + idempotency check + handler dispatch template.

# Failure handling
On signature failure, return 401 and log. On processing failure, enqueue for retry. Never return 500 to the webhook sender after acknowledging receipt.
