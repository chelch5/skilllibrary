---
name: nextjs-app-router
description: Handles route structure, server/client component boundaries, data fetching, and deployment caveats for Next.js App Router projects. Trigger when building or debugging a Next.js App Router app. Do NOT use for Next.js Pages Router projects.
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
  tags: [nextjs, app-router, server-components]
---

# Purpose
Guides Next.js App Router development with correct server/client component boundaries, data fetching patterns, and deployment-aware conventions.

# When to use this skill
Use when:
- Building a Next.js application using the App Router (app/ directory)
- Debugging server/client component boundary errors or data fetching issues

Do NOT use when:
- Using the Pages Router (pages/ directory)
- Building a non-Next.js React application

# Operating procedure
1. Structure routes in the `app/` directory with correct layout nesting
2. Mark components as Server or Client components explicitly
3. Fetch data in Server components using async/await; avoid client-side fetching where unnecessary
4. Handle loading and error states using `loading.tsx` and `error.tsx` conventions
5. Test for SSR/edge deployment compatibility before shipping

# Output defaults
Next.js App Router page and layout files with correct server/client boundaries and data fetching patterns.

# Failure handling
If a server component accidentally imports a client-only module, the build will fail. Use dynamic imports or move logic to a client component.
