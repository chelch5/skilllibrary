---
name: research-synthesis
description: Combines multiple sources into a grounded research report with findings, gaps, and recommendations. Use when synthesizing evidence from multiple inputs into a coherent output.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P0
  maturity: draft
  risk: low
  tags: [research, synthesis, analysis, reporting]
---

# Purpose
Combines multiple sources into a grounded research report with findings, gaps, and recommendations.

# When to use this skill
Use when:
- Synthesizing research from multiple documents or sources
- Writing a research summary with evidence citations
- Producing a findings report with gaps and next steps

Do NOT use when:
- Single-source summaries (simpler task)
- Purely creative writing without research basis

# Operating procedure
1. Collect and read all source materials
2. Identify common themes and contradictions across sources
3. Synthesize findings with explicit citation to sources
4. Identify knowledge gaps and open questions
5. Write structured report with recommendations

# Output defaults
Research report with sections: background, findings, gaps, recommendations, citations

# Failure handling
If sources contradict, note the contradiction explicitly. Don't resolve without basis.
