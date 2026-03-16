---
name: property-research
description: Researches property listings, market values, neighborhood data, and investment metrics for real estate decisions. Use when evaluating property purchases or rentals.
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
  tags: [property, real-estate, research, investment]
---

# Purpose
Researches property listings, market values, neighborhood data, and investment metrics for real estate decisions.

# When to use this skill
Use when:
- Researching property values and market trends for a location
- Evaluating a specific property for purchase or rental
- Comparing investment metrics across properties

Do NOT use when:
- Legal or financial advice (outside scope)
- Commercial real estate at enterprise scale

# Operating procedure
1. Define location and property criteria
2. Gather comparable sales or rental data
3. Analyze neighborhood metrics (amenities, transport, schools)
4. Calculate investment metrics (yield, cap rate if applicable)
5. Summarize recommendation with key factors

# Output defaults
Property research report with comparables, neighborhood data, and investment metrics

# Failure handling
If data is unavailable for a location, note the gap. Suggest alternative data sources.
