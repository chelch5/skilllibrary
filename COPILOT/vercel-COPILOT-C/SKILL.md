---
name: vercel
description: Applies Vercel deployment, routing, runtime, and environment conventions for web applications. Use when deploying frontend apps or serverless functions to Vercel.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cloud-platform-devops
  priority: P2
  maturity: draft
  risk: low
  tags: [vercel, deployment, frontend, serverless]
---

# Purpose
Applies Vercel deployment, routing, runtime, and environment conventions for web applications.

# When to use this skill
Use when:
- Deploying a Next.js, Vite, or static site to Vercel
- Configuring Vercel environment variables and routes
- Setting up preview deployments for PRs

Do NOT use when:
- Backend-heavy applications better suited to container deployment
- Projects that require persistent server state or long-running processes

# Operating procedure
1. Configure vercel.json with rewrites and headers
2. Set environment variables per environment (preview/prod)
3. Validate build output and function size limits
4. Test preview deployment before promoting
5. Document domain and DNS configuration

# Output defaults
vercel.json configs, environment variable docs, deployment URLs, build logs

# Failure handling
If build fails, check framework detection and output directory settings.
