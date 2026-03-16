---
name: business-idea-evaluation
description: Evaluates business ideas against market size, competition, feasibility, and strategic fit. Use when assessing whether an idea is worth pursuing or investing in.
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
  tags: [business, evaluation, market-fit, strategy]
---

# Purpose
Evaluates business ideas against market size, competition, feasibility, and strategic fit.

# When to use this skill
Use when:
- Evaluating a new business idea or startup concept
- Assessing market size and competitive landscape
- Deciding whether to build vs buy vs partner

Do NOT use when:
- Pure technical feasibility analysis (different scope)
- Personal financial planning without business context

# Operating procedure
1. Define the problem and target customer clearly
2. Estimate market size (TAM/SAM/SOM)
3. Identify top competitors and differentiation
4. Assess feasibility with available resources
5. Summarize go/no-go recommendation with reasoning

# Output defaults
Business idea evaluation doc with market sizing, competitive analysis, and recommendation

# Failure handling
If data is unavailable, document assumptions explicitly. Validate key assumptions first.
