---
name: terminal-debugging
description: Uses focused terminal inspection to diagnose environment, process, path, and runtime problems. Use when something works on one machine but fails on another. Do NOT use for application-level API debugging.
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
  tags: [debugging, terminal, environment, process, path]
---

# Purpose
Provides a systematic terminal debugging checklist covering environment variables, PATH, process state, file permissions, and network connectivity.

# When to use this skill
Use when:
- A command fails with a confusing error message
- Environment differences between machines cause failures
- Debugging PATH, permissions, or missing dependencies

Do NOT use when:
- Application-level HTTP debugging (use api-debugging)
- Proxmox or virtualisation-specific issues

# Operating procedure
1. Check environment: env | grep RELEVANT_VAR
2. Verify binary location: which cmd && cmd --version
3. Inspect file permissions: ls -la file && stat file
4. Check process state: ps aux | grep process && lsof -p PID
5. Test network: ping, curl -v, nc -zv host port
6. Review recent logs: journalctl -n 50 or tail -f /var/log/app.log

# Output defaults
Diagnostic command sequence + environment checklist + common fix patterns.

# Failure handling
Document each check result before moving to the next. If the issue is intermittent, add logging and reproduce before fixing.
