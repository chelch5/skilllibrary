---
name: secret-management
description: Handles environment variables, secret storage, rotation, and accidental exposure prevention. Prevents secrets from ending up in code, logs, or public repositories.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cloud-platform-devops
  priority: P1
  maturity: draft
  risk: low
  tags: [secrets, environment-variables, security, devops]
---

# Purpose
Handles environment variables, secret storage, rotation, and accidental exposure prevention.

# When to use this skill
Use when:
- Setting up secret management for a new project
- Auditing for accidentally committed secrets
- Implementing secret rotation workflows

Do NOT use when:
- Public configuration values that don't need protection
- Cryptography implementation (a different concern)

# Operating procedure
1. Audit codebase for hardcoded secrets
2. Configure secrets manager (AWS Secrets Manager, Vault, or .env)
3. Add pre-commit hooks to prevent secret commits
4. Document secret rotation procedure
5. Validate secrets are never logged

# Output defaults
Secrets management configs, pre-commit hook setup, rotation runbooks

# Failure handling
If a secret is exposed, rotate it immediately. Audit access logs for unauthorized use.
