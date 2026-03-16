---
name: cloudflare-worker-patterns
description: A specialized skill for Cloudflare Workers runtime patterns covering request handling, KV storage, Durable Objects, and edge-specific constraints. Use when building Workers applications.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cloud-platform-devops
  priority: P2
  maturity: draft
  risk: low
  tags: [cloudflare-workers, edge-computing, serverless, kv]
---

# Purpose
A specialized skill for Cloudflare Workers runtime patterns covering request handling, KV storage, Durable Objects, and edge-specific constraints.

# When to use this skill
Use when:
- Building or debugging Cloudflare Worker scripts
- Implementing KV, R2, or Durable Object patterns
- Optimizing Worker performance within CPU/memory limits

Do NOT use when:
- Full server deployments outside the Workers runtime
- Workers with simple proxy patterns (use cloudflare skill instead)

# Operating procedure
1. Structure Worker with proper request routing
2. Apply KV or Durable Objects for state management
3. Handle CPU time limits and streaming responses
4. Write integration tests with Miniflare
5. Document bindings and environment variables

# Output defaults
Worker scripts, wrangler.toml configs, KV/Durable Object binding docs

# Failure handling
If Worker times out, profile CPU usage. Split work across multiple subrequests.
