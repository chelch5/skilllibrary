---
name: realtime-websocket
description: Applies connection lifecycle, message schema, fanout, and failure handling to realtime systems. Use when building WebSocket or SSE-based features. Do NOT use for simple request-response APIs.
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
  tags: [websocket, realtime, sse, fanout, streaming]
---

# Purpose
Establishes reliable WebSocket connection management, message framing, fanout, and graceful reconnect patterns.

# When to use this skill
Use when:
- Building a chat, live feed, or collaborative feature over WebSocket
- Designing a Server-Sent Events stream
- Adding reconnect and backpressure logic to a realtime client

Do NOT use when:
- Simple request/response HTTP APIs suffice
- One-way bulk data transfer (use streaming HTTP instead)

# Operating procedure
1. Define typed message schema (JSON with type discriminator)
2. Implement heartbeat ping/pong with configurable interval
3. Handle connection close: clean shutdown vs error disconnect
4. Fanout via pub/sub broker (Redis, NATS) not in-process memory
5. Client: reconnect with exponential backoff, replay missed messages
6. Rate-limit inbound messages per connection

# Output defaults
Message schema + server handler skeleton + client reconnect logic.

# Failure handling
On server crash, clients reconnect and receive a replay cursor. On message parse error, send error frame and close connection cleanly.
