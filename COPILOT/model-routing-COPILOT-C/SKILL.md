---
name: model-routing
description: Routes different requests to different models or runtimes based on capability, latency, or cost. Use when operating a fleet of models. Do NOT use for single-model integrations.
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
  tags: [routing, models, cost, latency, fleet]
---

# Purpose
Designs a routing layer that directs requests to the most appropriate model based on task type, cost budget, and latency requirements.

# When to use this skill
Use when:
- Running multiple models (local + cloud, fast + slow)
- Implementing cost-optimised routing: simple tasks to cheap models
- Adding cascade routing: cheap model first, escalate on low confidence

Do NOT use when:
- Single-model, single-provider integration (use llm-integration)
- Static model selection with no runtime decision needed

# Operating procedure
1. Classify requests by task type (summarise, code, reason, classify)
2. Map task types to preferred models with fallback order
3. Implement cascade: primary model → judge confidence → escalate if below threshold
4. Track cost and latency per route in metrics
5. Add circuit breaker per model endpoint
6. Allow override via request metadata for power users

# Output defaults
Routing config map + classifier + cascade logic + metrics hook.

# Failure handling
If primary and all fallback models fail, return a degraded response or error. Log routing decisions with request ID for audit.
