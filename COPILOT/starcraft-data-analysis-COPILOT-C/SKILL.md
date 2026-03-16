---
name: starcraft-data-analysis
description: Analyzes StarCraft 2 replay data, player statistics, build orders, and match outcomes for performance insights. Specialized for SC2 data pipelines and game analysis.
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
  tags: [starcraft, gaming, data-analysis, esports]
---

# Purpose
Analyzes StarCraft 2 replay data, player statistics, build orders, and match outcomes for performance insights.

# When to use this skill
Use when:
- Analyzing StarCraft 2 replay files or match data
- Building SC2 player performance statistics and trends
- Researching build orders and strategic patterns from replays

Do NOT use when:
- Other RTS or esports data without SC2 specifics
- General game data analytics without SC2 context

# Operating procedure
1. Load replay or match data from source
2. Extract player actions, build orders, and APM metrics
3. Aggregate statistics by player, race, or map
4. Identify patterns and strategic tendencies
5. Produce summary with charts or tables

# Output defaults
SC2 analysis report with player stats, build order frequencies, and pattern findings

# Failure handling
If replay parsing fails, validate replay file version compatibility.
