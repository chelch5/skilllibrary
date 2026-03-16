---
name: cost-monitoring
description: Tracks cloud, model, and infrastructure costs and highlights runaway spending patterns before they become problems. Use when cost visibility or budget enforcement is needed.
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
  tags: [cost, monitoring, cloud-costs, budget]
---

# Purpose
Tracks cloud, model, and infrastructure costs and highlights runaway spending patterns before they become problems.

# When to use this skill
Use when:
- Setting up cloud cost monitoring and alerts
- Investigating unexpected cost spikes
- Implementing cost tagging and allocation strategies

Do NOT use when:
- On-premise infrastructure with fixed costs
- Application performance monitoring (not cost-related)

# Operating procedure
1. Enable cost explorer and billing alerts
2. Apply resource tagging strategy for cost allocation
3. Set budget thresholds with notification actions
4. Review top cost drivers weekly
5. Document cost baseline and anomaly thresholds

# Output defaults
Cost dashboard configs, tagging policies, budget alert rules, cost reports

# Failure handling
If costs spike unexpectedly, identify the resource immediately and apply stop/scale-down.
