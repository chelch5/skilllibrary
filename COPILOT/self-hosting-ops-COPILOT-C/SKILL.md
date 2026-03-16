---
name: self-hosting-ops
description: Covers deployment, upgrade, backup, and operational safety for self-hosted services on VPS or bare-metal. Use for headless server or homelab deployments.
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
  tags: [self-hosting, vps, server-ops, linux]
---

# Purpose
Covers deployment, upgrade, backup, and operational safety for self-hosted services on VPS or bare-metal.

# When to use this skill
Use when:
- Deploying self-hosted services on a VPS or dedicated server
- Setting up backups and monitoring for self-hosted apps
- Upgrading or migrating self-hosted services safely

Do NOT use when:
- Managed cloud services where the provider handles ops
- Kubernetes or container orchestration clusters

# Operating procedure
1. Provision server with hardened base config
2. Deploy service with reverse proxy (nginx/Caddy)
3. Configure systemd service and automatic restart
4. Set up backup schedule and offsite copy
5. Monitor with uptime checks and log rotation

# Output defaults
Server setup scripts, nginx/Caddy configs, systemd unit files, backup cron jobs

# Failure handling
If service fails to start, check systemd logs. Validate port availability and file permissions.
