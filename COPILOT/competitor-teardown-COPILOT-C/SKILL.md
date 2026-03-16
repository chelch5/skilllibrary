---
name: competitor-teardown
description: Performs structured competitive analysis on products, features, pricing, and positioning. Produces actionable insights rather than raw data dumps.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: business-research-and-optional-domains
  priority: P2
  maturity: draft
  risk: low
  tags: [competitive-analysis, research, strategy, market]
---

# Purpose
Performs structured competitive analysis on products, features, pricing, and positioning.

# When to use this skill
Use when:
- Analyzing a competitor's product, pricing, or positioning
- Building a competitive landscape map
- Identifying gaps and opportunities in a market

Do NOT use when:
- Internal product analysis without competitor context
- Legal or financial due diligence (different scope)

# Operating procedure
1. Identify top competitors to analyze
2. Collect data on features, pricing, messaging, reviews
3. Structure findings by dimension (product, price, reach)
4. Identify competitor strengths and weaknesses
5. Summarize strategic implications and opportunities

# Output defaults
Competitive analysis matrix with dimensions, findings, and strategic implications

# Failure handling
If competitor data is incomplete, note gaps. Never fabricate competitor capabilities.
