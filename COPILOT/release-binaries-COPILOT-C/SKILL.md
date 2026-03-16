---
name: release-binaries
description: Packages compiled CLI artifacts, checksums, and release metadata for distribution. Use when automating binary releases via CI. Do NOT use for interpreted language packaging.
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
  tags: [release, binaries, goreleaser, checksums, github-releases]
---

# Purpose
Automates multi-platform binary builds, checksum generation, and GitHub Release uploads for compiled CLI tools.

# When to use this skill
Use when:
- Setting up GoReleaser or a similar tool for a Go CLI
- Adding checksum files and signed releases
- Defining release artifact naming conventions

Do NOT use when:
- Python/npm package releases (use packaging-installers or language skills)
- Container image publishing

# Operating procedure
1. Use GoReleaser with .goreleaser.yml for Go projects
2. Build for linux/amd64, linux/arm64, darwin/amd64, darwin/arm64, windows/amd64
3. Generate SHA256SUMS file alongside binaries
4. Attach release notes from CHANGELOG or git log
5. Sign releases with cosign or GPG for supply-chain integrity
6. Tag with semver before triggering release workflow

# Output defaults
.goreleaser.yml + GitHub Actions release workflow + checksum verification step.

# Failure handling
If any platform build fails, abort the entire release to prevent partial artifacts. Verify checksums in CI before uploading to GitHub Releases.
