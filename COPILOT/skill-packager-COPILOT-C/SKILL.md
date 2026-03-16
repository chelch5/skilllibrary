---
name: skill-packager
description: "Builds distributable bundles, manifests, and checksums for installing or sharing skills. Useful if you want a portable library instead of raw markdown folders. Trigger when the task context clearly involves skill packager."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P1
  maturity: draft
  risk: low
  tags: [packaging, bundle, distribution]
---

# Purpose
Orchestrates the full packaging process for one or more skills: validates readiness, applies the packaging procedure to each, builds an index, and produces a release-ready bundle or registry submission.

# When to use this skill
Use when:
- The user says "package these skills for release", "build a skill bundle", or "prepare a skill library release"
- Multiple skills need to be packaged together as a named release (e.g. a skill pack for a specific domain)
- A library is being published and all skills need manifests, checksums, and an index generated
- An automated packaging pipeline is being set up

Do NOT use when:
- A single skill needs to be packaged (use `skill-packaging` directly)
- The goal is installation, not packaging (use `skill-installation`)
- The skills have not yet been reviewed or validated

# Operating procedure
1. **Collect the skill list**: Enumerate all skills to be packaged — either from a provided list or by scanning a directory
2. **Run pre-packaging validation on each skill**:
   - SKILL.md present with complete frontmatter
   - No anti-pattern content (check `skill-anti-patterns`)
   - maturity field is `stable` or explicitly approved as `draft` for inclusion
   - If any skill fails validation, add it to a **Blocked** list with the reason
3. **Apply `skill-packaging` procedure to each validated skill**: Generate manifest.json and zip bundle per skill
4. **Build the pack index** (`index.json` at the root of the bundle):
   - `pack_name`, `pack_version`, `created_at`
   - `skills`: array of { name, version, file, checksum, tags } for each packaged skill
   - `blocked`: list of skills that failed validation with reasons
5. **Bundle all zips and the index into a top-level archive**: `PACKNAME-VERSION.tar.gz` or `.zip`
6. **Generate a release manifest**: Human-readable `RELEASE.md` listing what is in the bundle, what was blocked, and any important compatibility notes
7. **Verify the complete bundle**: Spot-check 2–3 skills from the bundle by extracting and verifying their manifests

# Output defaults
Individual skill `.zip` files, a pack `index.json`, a `RELEASE.md`, and a top-level bundle archive. A **Packaging Report** stating how many skills were packaged, how many were blocked, and total bundle size.

# Failure handling
If more than 20% of skills fail validation, halt and report the failure rate rather than proceeding with a partial bundle. Partial bundles without clear documentation of what was excluded cause more harm than a full halt.
