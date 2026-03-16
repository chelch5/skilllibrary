---
name: market-research
description: Conducts structured market research covering size, segments, trends, and customer needs. Produces grounded findings rather than speculative summaries.
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
  tags: [market-research, analysis, trends, research]
---

# Purpose
Conducts structured market research covering size, segments, trends, and customer needs.

# When to use this skill
Use when:
- Researching a market segment for a new product or feature
- Analyzing market trends and customer behavior
- Sizing a market opportunity with supporting evidence

Do NOT use when:
- Internal product analytics (a different scope)
- Pure competitor analysis (use competitor-teardown instead)

# Operating procedure
1. Define research questions and scope
2. Identify primary and secondary data sources
3. Collect and analyze market size and segment data
4. Synthesize trends and customer pain points
5. Document findings with source citations

# Output defaults
Market research report with market sizing, segments, trends, and customer needs summary

# Failure handling
If data sources conflict, present both with confidence levels. Flag unreliable sources.
