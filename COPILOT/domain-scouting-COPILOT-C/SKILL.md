---
name: domain-scouting
description: Scouts domain name availability, evaluates naming options, and researches trademark considerations for new projects. Use when choosing a name or domain for a product.
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
  tags: [domains, naming, branding, research]
---

# Purpose
Scouts domain name availability, evaluates naming options, and researches trademark considerations for new projects.

# When to use this skill
Use when:
- Finding available domain names for a new project
- Evaluating naming options for brand coherence
- Checking trademark conflicts for a product name

Do NOT use when:
- Technical infrastructure setup (different from naming)
- SEO optimization for existing domains

# Operating procedure
1. Generate name candidates matching brand goals
2. Check domain availability across TLDs
3. Verify social handle availability
4. Screen for trademark conflicts
5. Summarize top recommendations with rationale

# Output defaults
Domain availability report, name recommendations with rationale, trademark notes

# Failure handling
If preferred domain is taken, suggest alternatives. Document why each option was considered.
