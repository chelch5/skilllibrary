---
name: inference-serving
description: Covers API serving, concurrency, queuing, batching, and operational behaviour for hosted LLM inference. Use when deploying a model behind an HTTP API. Do NOT use for local single-user inference.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-runtime-and-integration
  priority: P1
  maturity: draft
  risk: low
  tags: [inference, serving, api, batching, concurrency]
---

# Purpose
Designs production inference serving with request queuing, continuous batching, timeout handling, and health monitoring.

# When to use this skill
Use when:
- Deploying a model with vLLM, TGI, Triton, or a custom server
- Designing request queue and batch sizing for throughput
- Adding health checks, autoscaling triggers, and graceful shutdown

Do NOT use when:
- Local single-user inference (use local-llm or ollama)
- Batch offline processing without latency requirements

# Operating procedure
1. Choose serving backend: vLLM (high throughput), Ollama (local), TGI (HF ecosystem)
2. Set max_concurrent_requests and queue depth based on GPU memory
3. Enable continuous batching where supported
4. Add /health and /ready endpoints; wire to load balancer
5. Set per-request timeout and max tokens to prevent runaway costs
6. Expose token/s and queue depth metrics to monitoring

# Output defaults
Serving config + health endpoint + queue/timeout settings + metrics exposure.

# Failure handling
On OOM error, reduce batch size and restart. On queue saturation, return 503 with Retry-After header. Log all inference errors with request ID.
