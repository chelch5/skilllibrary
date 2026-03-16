---
name: frontend-webapp-builder
description: A frontend web app builder skill covering component architecture, state management, build tooling, and deployment patterns. Use when scaffolding or building frontend web applications.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: external-reference-seeds
  priority: P2
  maturity: draft
  risk: low
  tags: [frontend, webapp, react, build]
---

# Purpose
A frontend web app builder skill covering component architecture, state management, build tooling, and deployment patterns.

# When to use this skill
Use when:
- Scaffolding or building a frontend web application
- Setting up build tooling (Vite, Webpack, Next.js)
- Implementing component architecture and state management

Do NOT use when:
- Backend-only services without frontend components
- Native mobile or desktop apps

# Operating procedure
1. Define component hierarchy and data flow
2. Set up build tooling with appropriate framework
3. Implement state management pattern
4. Configure routing and code splitting
5. Set up deployment pipeline to hosting target

# Output defaults
Component structure, build configs, routing setup, deployment configuration

# Failure handling
If bundle size is large, analyze with bundle analyzer. Apply code splitting.
