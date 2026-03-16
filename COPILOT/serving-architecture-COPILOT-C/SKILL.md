---
name: serving-architecture
description: Designs the end-to-end architecture for serving LLMs at scale including load balancing, KV cache, and autoscaling. Use when designing a production LLM serving system. Do NOT use for single-model inference config.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-training-architecture-and-research
  priority: P1
  maturity: draft
  risk: low
  tags: [serving, architecture, kv-cache, autoscaling, load-balancing]
---

# Purpose
Designs production LLM serving architecture with prefix caching, load balancing, autoscaling triggers, and SLA-driven capacity planning.

# When to use this skill
Use when:
- Designing a multi-replica LLM serving deployment
- Planning KV cache sharing and prefix caching strategy
- Setting autoscaling policies based on queue depth and GPU utilisation

Do NOT use when:
- Single-instance vLLM or Ollama config (use vllm-serving or inference-serving)
- Model architecture design (use model-architecture)

# Operating procedure
1. Define SLA: target latency p50, p99, and throughput (requests/sec)
2. Size replica count based on peak load and model VRAM footprint
3. Implement load balancer with session affinity for KV cache reuse
4. Enable prefix caching for shared system prompts
5. Set autoscaling: scale up at queue depth >10, scale down at <2 for 5 minutes
6. Add graceful shutdown: drain in-flight requests before terminating a replica

# Output defaults
Serving architecture diagram + autoscaling config + capacity planning table + SLA monitoring queries.

# Failure handling
On replica OOM, reduce --max-num-seqs and alert. On SLA breach at peak load, trigger emergency scale-up and add capacity to autoscaling ceiling.
