---
name: frontend-performance
description: Analyzes bundle size, loading strategy, rendering cost, image handling, and user-perceived responsiveness. Trigger when a web app has performance issues or during a performance audit. Do NOT use for backend API performance.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P1
  maturity: draft
  risk: low
  tags: [performance, bundle, rendering]
---

# Purpose
Identifies and resolves frontend performance issues across bundle size, loading strategy, rendering cost, and user-perceived responsiveness.

# When to use this skill
Use when:
- A web app is slow to load or interact with and needs a performance audit
- Optimizing bundle size or improving Core Web Vitals scores

Do NOT use when:
- Profiling backend API latency (use backend tooling)
- General code quality review

# Operating procedure
1. Measure baseline with Lighthouse or equivalent (LCP, FID, CLS, TTI)
2. Analyze bundle with a bundle analyzer to find large or duplicated dependencies
3. Apply code splitting and lazy loading for routes and heavy components
4. Optimize images with next-gen formats, lazy loading, and correct sizing
5. Measure again after each change to confirm improvement

# Output defaults
A performance report with baseline metrics, identified bottlenecks, applied optimizations, and post-optimization metrics.

# Failure handling
If an optimization regresses another metric, revert the change and document the tradeoff before trying an alternative approach.
