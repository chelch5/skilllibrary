---
name: proxmox-shell-scripting
description: Applies shell automation patterns in a Proxmox or virtualisation-heavy environment. Use when writing scripts to manage Proxmox VMs, LXC containers, or storage. Do NOT use for general Linux sysadmin tasks.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cli-systems-and-ops
  priority: P2
  maturity: draft
  risk: low
  tags: [proxmox, virtualisation, lxc, vm, shell, automation]
---

# Purpose
Provides scripting patterns for Proxmox VE: VM/LXC lifecycle, storage management, backup, and cluster operations via pvesh and pvesm.

# When to use this skill
Use when:
- Automating Proxmox VM or LXC container creation
- Writing backup or snapshot scripts against Proxmox storage
- Querying cluster status via pvesh API

Do NOT use when:
- General Ubuntu Linux ops not involving Proxmox (use linux-ubuntu-ops)
- Cloud provider VMs (AWS, GCP, Azure)

# Operating procedure
1. Use pvesh for API calls; prefer JSON output with --output-format json
2. Authenticate via API token (PVEAPIToken), not root password in scripts
3. Check node/cluster health with pvesh get /nodes before bulk operations
4. Snapshot VMs before destructive operations; verify snapshot exists
5. Use set -euo pipefail in all automation scripts
6. Log operations with timestamps to /var/log/proxmox-automation.log

# Output defaults
pvesh command examples + VM/LXC lifecycle script + snapshot-before-destroy pattern.

# Failure handling
On pvesh API error, log response body and exit. On lock contention (task queue full), retry after delay. Never force-delete a VM without a verified snapshot.
