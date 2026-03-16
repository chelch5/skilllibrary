---
name: react-typescript
description: Defines component patterns, typing conventions, state boundaries, and validation expectations for React+TypeScript projects. Trigger when building or reviewing React TypeScript components. Do NOT use for Vue, Svelte, or non-TypeScript React projects.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P0
  maturity: draft
  risk: low
  tags: [react, typescript, components]
---

# Purpose
Provides React + TypeScript conventions for component structure, prop typing, state management boundaries, and validation patterns.

# When to use this skill
Use when:
- Building new React components in a TypeScript project
- Reviewing React+TypeScript code for type safety and component design quality

Do NOT use when:
- Working in Vue or Svelte (use their respective skills)
- Using React without TypeScript

# Operating procedure
1. Define component props with explicit TypeScript interfaces
2. Separate presentational and container components
3. Use React hooks for local state; avoid class components
4. Apply strict TypeScript: no `any`, use discriminated unions for variant props
5. Validate form and API data at the boundary using Zod or similar

# Output defaults
React components with full TypeScript typing, clear prop interfaces, and hook-based state management.

# Failure handling
If a type error cannot be resolved cleanly, add a comment explaining the workaround. Never suppress with `@ts-ignore` without explanation.
