---
name: asset-pipeline
description: Standardizes asset sourcing, naming, versioning, import settings, and optimization for game projects. Prevents asset chaos across team or solo development.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: game-engines-and-creative-tech
  priority: P1
  maturity: draft
  risk: low
  tags: [assets, pipeline, import, optimization]
---

# Purpose
Standardizes asset sourcing, naming, versioning, import settings, and optimization for game projects.

# When to use this skill
Use when:
- Setting up asset import conventions for a game project
- Optimizing texture, audio, or mesh assets
- Establishing asset naming and folder structure

Do NOT use when:
- Software projects without media assets
- Web projects using standard image formats only

# Operating procedure
1. Define asset naming conventions by type
2. Configure engine import settings (compression, mip maps)
3. Set up LOD rules for meshes
4. Automate atlas generation for 2D sprites
5. Document asset budget targets per platform

# Output defaults
Asset naming guides, import configuration files, optimization reports, folder structure templates

# Failure handling
If assets cause build size bloat, run asset audit tool. Identify unreferenced assets.
