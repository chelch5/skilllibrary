---
name: systemd-services
description: Creates and maintains systemd units, restart behaviour, logging, and safe service deployment. Use when running a process as a managed Linux service. Do NOT use for container orchestration.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cli-systems-and-ops
  priority: P2
  maturity: draft
  risk: low
  tags: [systemd, service, linux, daemon, unit-file]
---

# Purpose
Produces correct systemd unit files with least-privilege users, restart policies, and journald-integrated logging.

# When to use this skill
Use when:
- Running an application as a persistent background service on Linux
- Setting up auto-start, restart on failure, and graceful shutdown
- Reviewing a unit file for security hardening

Do NOT use when:
- Container orchestration (Docker, Kubernetes)
- Cloud function or Lambda-style workloads

# Operating procedure
1. Create unit file in /etc/systemd/system/appname.service
2. Set User= and Group= to a dedicated system account
3. Set Restart=on-failure with RestartSec=5
4. Use StandardOutput=journal StandardError=journal
5. Add After=network.target and any DB service dependency
6. Run systemctl daemon-reload && systemctl enable --now appname

# Output defaults
.service unit file + install instructions + journalctl monitoring commands.

# Failure handling
On service crash loop, check journalctl -u appname -n 50. Add StartLimitIntervalSec and StartLimitBurst to prevent runaway restarts.
