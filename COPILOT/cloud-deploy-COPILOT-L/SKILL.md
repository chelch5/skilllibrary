---
name: cloud-deploy
description: A broad deployment skill for selecting and applying cloud deployment targets cleanly across providers. Use when standardizing or automating cloud release workflows.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cloud-platform-devops
  priority: P2
  maturity: draft
  risk: low
  tags: [deployment, cloud, ci-cd, release]
---

# Purpose
A broad deployment skill for selecting and applying cloud deployment targets cleanly across providers.

# When to use this skill
Use when:
- Standardizing deployment workflows across cloud providers
- Automating release pipelines to cloud targets
- Choosing deployment strategies (blue/green, canary, rolling)

Do NOT use when:
- Local development deployments
- Highly provider-specific deployments (use aws or gcp skills instead)

# Operating procedure
1. Identify deployment target and strategy
2. Define rollout stages and health checks
3. Automate with CI/CD pipeline integration
4. Implement rollback mechanism
5. Document release checklist and monitoring

# Output defaults
Deployment pipeline configs, release strategy docs, rollback runbooks

# Failure handling
If deployment fails, execute rollback immediately. Investigate root cause before retry.
