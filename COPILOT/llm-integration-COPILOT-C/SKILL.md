---
name: llm-integration
description: Integrates AI capabilities into a product or service with safe boundaries, cost awareness, and useful UX. Use when adding LLM calls to an application. Do NOT use for model training or deployment.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-runtime-and-integration
  priority: P0
  maturity: draft
  risk: low
  tags: [llm, integration, openai, api, product]
---

# Purpose
Provides safe, cost-aware patterns for integrating LLM calls into products: prompt management, cost tracking, fallback, and user-facing error handling.

# When to use this skill
Use when:
- Adding OpenAI, Anthropic, or other LLM API calls to a product
- Designing prompt templates with version control
- Adding cost controls, fallback models, and user-visible error handling

Do NOT use when:
- Running local models (use local-llm or ollama)
- Model fine-tuning or training

# Operating procedure
1. Abstract provider behind a thin client interface for swappability
2. Version and test prompt templates independently of code
3. Set max_tokens and timeout on every call; never leave unbounded
4. Track cost per call (token counts * price); alert on anomalies
5. Add fallback: primary model failure → cheaper/faster backup model
6. Return graceful user error on LLM failure; never surface raw API errors

# Output defaults
Provider client abstraction + prompt template versioning + cost tracking snippet + fallback config.

# Failure handling
On API error, retry once with backoff then fall back. On rate limit, queue and retry. Log all failures with prompt hash for debugging without leaking content.
