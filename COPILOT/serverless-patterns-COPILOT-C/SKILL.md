---
name: serverless-patterns
description: Applies serverless design patterns including cold-start awareness, event structure, stateless boundaries, and idempotency. Use when building or reviewing serverless function architectures.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cloud-platform-devops
  priority: P1
  maturity: draft
  risk: low
  tags: [serverless, functions, event-driven, cold-start]
---

# Purpose
Applies serverless design patterns including cold-start awareness, event structure, stateless boundaries, and idempotency.

# When to use this skill
Use when:
- Designing serverless function architectures
- Optimizing cold start performance
- Implementing event-driven workflows with functions

Do NOT use when:
- Always-on services where serverless adds unnecessary complexity
- Stateful services requiring persistent connections

# Operating procedure
1. Define function boundaries and event contracts
2. Implement idempotency for all handler logic
3. Optimize cold start (minimize dependencies, use provisioned concurrency if needed)
4. Add structured logging and distributed tracing
5. Test with event payload mocks

# Output defaults
Function handler code, event schema definitions, deployment configs, performance benchmarks

# Failure handling
If cold starts are too slow, reduce bundle size or enable provisioned concurrency.
