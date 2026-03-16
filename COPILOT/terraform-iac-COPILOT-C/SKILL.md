---
name: terraform-iac
description: Defines infrastructure-as-code structure using Terraform with modules, environments, and safe change patterns. Prevents infrastructure drift through code-first provisioning.
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
  tags: [terraform, iac, infrastructure, devops]
---

# Purpose
Defines infrastructure-as-code structure using Terraform with modules, environments, and safe change patterns.

# When to use this skill
Use when:
- Provisioning cloud infrastructure with Terraform
- Designing Terraform module structure for multiple environments
- Reviewing terraform plan output before apply

Do NOT use when:
- Application-level code not related to infrastructure
- Manual console-based infrastructure without IaC

# Operating procedure
1. Define module structure with variables and outputs
2. Separate environment configurations (dev/staging/prod)
3. Run terraform plan and review changes
4. Use remote state with locking (S3+DynamoDB or Terraform Cloud)
5. Document sensitive variables and state management

# Output defaults
Terraform module files, variable definitions, state config, plan outputs

# Failure handling
Never run terraform apply without reviewing plan. Use workspaces for env isolation.
