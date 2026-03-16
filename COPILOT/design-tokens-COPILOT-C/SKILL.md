---
name: design-tokens
description: Defines colors, spacing, typography, radius, and semantic token layers for consistent, reusable design systems. Trigger when establishing or auditing a design token system. Do NOT use for one-off component styling.
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
  tags: [design-tokens, design-system, theming]
---

# Purpose
Establishes a structured design token system covering primitive and semantic tokens for colors, spacing, typography, and shape.

# When to use this skill
Use when:
- Setting up a design system or theming layer for a web app
- Auditing inconsistent styling that could be consolidated into tokens

Do NOT use when:
- Styling a single one-off component without a design system context
- Working in a CSS-in-JS framework with its own token system already in place

# Operating procedure
1. Define primitive tokens (raw values: color-100, space-4, radius-sm)
2. Define semantic tokens that reference primitives (color-primary: color-600, spacing-card: space-4)
3. Map semantic tokens to component-level usage (button-background, input-border)
4. Export tokens in all required formats (CSS variables, JSON, Tailwind config)
5. Document token usage guidelines and prohibit direct primitive use in components

# Output defaults
A token definition file in CSS variables and JSON, with a documentation table of semantic token meanings.

# Failure handling
If a token is missing for a needed style, add it to the semantic layer first rather than hardcoding values in component styles.
