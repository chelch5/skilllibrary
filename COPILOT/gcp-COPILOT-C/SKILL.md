---
name: gcp
description: Applies GCP service selection, IAM, deployment, and operational patterns for cloud-backed workloads. Covers Cloud Run, GKE, BigQuery, Firestore, and related services.
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
  tags: [gcp, google-cloud, cloud, infrastructure]
---

# Purpose
Applies GCP service selection, IAM, deployment, and operational patterns for cloud-backed workloads.

# When to use this skill
Use when:
- Project deploys to or integrates with GCP
- Designing GCP IAM and service accounts
- Choosing between GCP services for a given workload

Do NOT use when:
- AWS or Azure deployments
- General cloud concepts not specific to GCP

# Operating procedure
1. Identify target GCP services for the workload
2. Design IAM with least-privilege service accounts
3. Configure networking (VPC, firewall rules)
4. Set up logging and monitoring via Cloud Logging
5. Document quota limits and cost estimates

# Output defaults
GCP architecture diagrams, IAM configs, Cloud Run/GKE manifests, cost estimates

# Failure handling
If permissions are denied, check IAM bindings and service account roles via gcloud.
