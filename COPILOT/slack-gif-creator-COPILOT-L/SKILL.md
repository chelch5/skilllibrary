---
name: slack-gif-creator
description: Creates short animated GIFs optimized for Slack or similar messaging platforms. A concrete example of a highly specific media-generation skill.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P2
  maturity: draft
  risk: low
  tags: [slack, gif, media, animation]
---

# Purpose
Creates short animated GIFs optimized for Slack or similar messaging platforms.

# When to use this skill
Use when:
- Creating animated GIFs for Slack reactions or announcements
- Generating looping animations for internal communication
- Producing short visual content for team messaging

Do NOT use when:
- Long-form video content
- Static image creation (use image-editor)

# Operating procedure
1. Define animation frames and loop behavior
2. Optimize GIF palette for target size (<2MB for Slack)
3. Set frame rate appropriate to animation speed
4. Preview loop in browser before export
5. Export with transparent background if needed

# Output defaults
Optimized GIF file under 2MB with correct loop settings for Slack upload

# Failure handling
If GIF is too large, reduce colors or frame count. Slack limit is 2MB.
