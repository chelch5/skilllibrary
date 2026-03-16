---
name: ssh-tmux-remote-workflow
description: Optimises remote CLI work with SSH, tmux session persistence, and safe long-running commands. Use when working interactively on remote servers. Do NOT use for automated CI pipelines.
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
  tags: [ssh, tmux, remote, terminal, session]
---

# Purpose
Provides reliable SSH configuration and tmux session management for long-running remote development workflows.

# When to use this skill
Use when:
- Setting up SSH config for multiple servers
- Managing long-running remote processes that must survive disconnection
- Configuring tmux for pair programming or persistent work sessions

Do NOT use when:
- Automated CI/CD pipelines (use systemd-services or cron)
- Proxmox-specific automation (use proxmox-shell-scripting)

# Operating procedure
1. Configure ~/.ssh/config with Host aliases, IdentityFile, and ServerAliveInterval
2. Use tmux new -s name to create named sessions; attach with tmux a -t name
3. Set TERM=screen-256color in .tmux.conf for colour support
4. Run long commands inside tmux so they survive SSH disconnection
5. Use ssh -A for agent forwarding only when necessary; disable after use
6. Copy files with rsync -avz --progress instead of scp for large transfers

# Output defaults
~/.ssh/config template + .tmux.conf base config + session management cheatsheet.

# Failure handling
On broken SSH connection, reconnect and reattach tmux session. If agent forwarding is needed, verify SSH_AUTH_SOCK is set before proceeding.
