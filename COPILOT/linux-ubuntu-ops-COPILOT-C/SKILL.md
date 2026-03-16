---
name: linux-ubuntu-ops
description: Applies practical Ubuntu/Linux server and workstation conventions for setup, services, paths, and troubleshooting. Use for Linux system operations. Do NOT use for cloud provider-specific infra.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cli-systems-and-ops
  priority: P1
  maturity: draft
  risk: low
  tags: [linux, ubuntu, ops, sysadmin, packages]
---

# Purpose
Provides reliable Ubuntu/Debian system administration patterns for package management, user setup, and service operations.

# When to use this skill
Use when:
- Setting up a new Ubuntu server or workstation
- Installing packages, managing users, or configuring paths
- Diagnosing system-level issues on Ubuntu

Do NOT use when:
- Cloud provider-specific infrastructure (use aws, gcp, or proxmox skills)
- Cross-platform scripts that must run on macOS or Windows

# Operating procedure
1. Use apt update && apt install -y; pin versions in production
2. Create dedicated service users with useradd --system --no-create-home
3. Place app binaries in /usr/local/bin; config in /etc/appname/
4. Set DEBIAN_FRONTEND=noninteractive for unattended installs
5. Use ufw for firewall; enable before exposing ports
6. Check journalctl -u servicename for service logs

# Output defaults
Setup script snippet + apt install commands + user and permission setup.

# Failure handling
On apt lock, wait or send SIGTERM to the holding process by PID. On missing package, check snap or manual deb install. Always verify with 'which' or 'systemctl status' after installation.
