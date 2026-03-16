---
name: theme-factory
description: Creates or refines a coherent visual theme as design tokens, CSS custom properties, or a component styling direction. Trigger when establishing or reskinning a product's visual identity. Do NOT use for per-component tweaks without a system intent (use frontend-design).
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P2
  maturity: stable
  risk: low
  tags: [theme, design-tokens, css-variables, branding, styling]
---

# Purpose
Produces a complete, consistent visual theme expressed as design tokens and component styling rules that can be applied across an entire product.

# When to use this skill
Use when:
- Building a new product that needs a visual identity from scratch
- Migrating a product from an old theme to a new one
- Creating a dark/light mode or brand variant

Do NOT use when:
- Only one component needs styling changes (use `frontend-design`)
- Brand guidelines already dictate all values (use `brand-guidelines` to apply them)

# Operating procedure
1. Define the token taxonomy: colour, typography, spacing, radius, shadow, motion
2. Set the colour palette: neutral scale (12 stops), brand primary, semantic (success/warning/error/info)
3. Set the type scale: 6-8 steps, base size, line-height and letter-spacing per step
4. Set the spacing scale: 4px base, geometric progression to ~64px
5. Define component tokens that reference the primitive tokens (e.g. `--button-bg: var(--color-primary-600)`)
6. Validate: check all text/background combinations meet WCAG AA contrast
7. Export as CSS custom properties, Tailwind config extension, or JSON token file

# Output defaults
Token file (CSS custom properties or JSON) + usage guide showing which token to use for which UI role.

# Failure handling
If a contrast check fails, adjust the lighter/darker stop rather than abandoning the colour choice. Document every override with rationale.
