---
name: aws
description: Applies AWS service selection, IAM policies, deployment patterns, and operational guardrails when AWS is the chosen cloud provider. Covers EC2, Lambda, S3, RDS, and related services.
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
  tags: [aws, cloud, iam, infrastructure]
---

# Purpose
Applies AWS service selection, IAM policies, deployment patterns, and operational guardrails when AWS is the chosen cloud provider.

# When to use this skill
Use when:
- Project deploys to or integrates with AWS
- Designing IAM roles and least-privilege policies
- Choosing between AWS services for a given workload

Do NOT use when:
- GCP or Azure deployments
- General cloud concepts not specific to AWS

# Operating procedure
1. Identify target AWS services for the workload
2. Design IAM roles with least-privilege policies
3. Configure networking (VPC, subnets, security groups)
4. Set up monitoring via CloudWatch
5. Document cost estimates and limits

# Output defaults
AWS architecture diagrams, IAM policies, CloudFormation/CDK templates, cost estimates

# Failure handling
If IAM permissions are denied, trace via CloudTrail. Never broaden policies blindly.
