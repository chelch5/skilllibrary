---
name: cloudflare
description: Covers Cloudflare products, constraints, deployment, and runtime patterns for projects using Cloudflare services. Includes DNS, CDN, Pages, and Workers.
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
  tags: [cloudflare, cdn, dns, edge]
---

# Purpose
Covers Cloudflare products, constraints, deployment, and runtime patterns for projects using Cloudflare services.

# When to use this skill
Use when:
- Configuring Cloudflare DNS, CDN, or security rules
- Deploying to Cloudflare Pages or Workers
- Setting up firewall rules and rate limiting

Do NOT use when:
- Non-Cloudflare infrastructure with different DNS providers
- Backend services not behind Cloudflare

# Operating procedure
1. Configure DNS records and proxy settings
2. Set up page rules or transform rules
3. Deploy to Cloudflare Pages with build settings
4. Configure security settings (WAF, rate limits)
5. Test with Cloudflare trace and analytics

# Output defaults
Cloudflare configuration exports, DNS zone files, worker scripts, firewall rules

# Failure handling
If requests fail at edge, check worker logs in dashboard. Validate cache rules.
