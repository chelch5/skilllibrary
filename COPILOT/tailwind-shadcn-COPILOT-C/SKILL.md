---
name: tailwind-shadcn
description: Standardizes utility-class styling, component composition, and design-system reuse using Tailwind CSS and shadcn/ui. Trigger when building UI with Tailwind and shadcn/ui. Do NOT use for custom CSS or CSS Modules projects.
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
  tags: [tailwind, shadcn, ui-components]
---

# Purpose
Provides conventions for using Tailwind CSS and shadcn/ui together to build consistent, reusable UI with minimal custom CSS.

# When to use this skill
Use when:
- Building UI components with Tailwind utility classes and shadcn/ui primitives
- Extending or customizing shadcn/ui components for a project's design system

Do NOT use when:
- Using CSS Modules, styled-components, or plain CSS
- Working with a different component library (MUI, Chakra)

# Operating procedure
1. Install and configure Tailwind CSS with the project's design tokens
2. Add shadcn/ui components via the CLI rather than copying manually
3. Extend components by composing shadcn primitives rather than overriding their styles
4. Use `cn()` for conditional class merging
5. Keep Tailwind classes readable by extracting complex class combinations into component variants

# Output defaults
Tailwind-styled components using shadcn/ui primitives with consistent variant patterns.

# Failure handling
If a shadcn component update breaks custom extensions, isolate the custom logic into a wrapper component to insulate it from upstream changes.
