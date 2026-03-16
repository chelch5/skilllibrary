---
name: tailscale-private-networking
description: Applies secure private networking patterns using Tailscale for multi-machine systems without exposing unnecessary attack surfaces. Use when services must communicate securely across networks.
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
  tags: [tailscale, vpn, networking, zero-trust]
---

# Purpose
Applies secure private networking patterns using Tailscale for multi-machine systems without exposing unnecessary attack surfaces.

# When to use this skill
Use when:
- Connecting multiple servers or services via Tailscale
- Replacing VPN or firewall rules with Tailscale ACLs
- Enabling secure access to self-hosted services

Do NOT use when:
- Public-facing services that need internet accessibility
- On-premise networks with existing VPN solutions

# Operating procedure
1. Install and authenticate Tailscale on all nodes
2. Define ACL policies in tailnet admin
3. Configure subnet routers if needed
4. Test connectivity between nodes
5. Document IP assignments and service access matrix

# Output defaults
Tailscale ACL configs, node connection diagrams, service access documentation

# Failure handling
If nodes can't connect, check ACL policies and MagicDNS settings in the admin console.
