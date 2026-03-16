---
name: project-skill-bootstrap
description: "Synthesizes project-local skills from the brief, stack, and domain signals instead of shipping only generic placeholders. This is the main answer to the 'bland skills' problem. Trigger when the task context clearly involves project skill bootstrap."
source: github.com/scafforge/session
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P0
  maturity: draft
  risk: low
  tags: [skills, bootstrap, project]
---

# Purpose
Synthesize project-specific skills from the brief, stack profile, and domain signals — replacing generic placeholders with skills that reference actual project files, libraries, and patterns.

# When to use this skill
Use when:
- A new project has been scaffolded with generic skill stubs that need to become project-aware
- A project's stack has changed significantly and its skills need to be updated
- An agent keeps producing generic code because it lacks project-specific guidance
- The user says "the skills don't know anything about this project" or "make the skills specific to X"

Do NOT use when:
- The project already has well-populated project-local skills
- Generic community skills are sufficient for the task at hand

# Operating procedure
1. **Load project context**: read AGENTS.md, the canonical brief, and any existing `.opencode/skills/`
2. **Run stack-profile-detector**: confirm language, framework, major libraries, test runner, lint config
3. **For each skill category**, generate a project-specific version:
   - **stack-standards**: replace generic rules with actual config file paths, library names, version constraints
   - **error-handling**: replace generic patterns with actual exception classes and logging library used
   - **testing**: replace generic advice with actual test runner commands, fixture locations, coverage thresholds
   - **api-schema**: replace generic OpenAPI boilerplate with actual endpoint list and schema types
4. **Add project-specific trigger phrases**: each skill must include phrases the agent will actually say in this project (e.g., "use the `UserRepository` class", not "use your data layer")
5. **Reference actual files**: every operating procedure step must cite a real file path where applicable
6. **Write skill files** to `.opencode/skills/` (project-local, overrides global skills)

# Output defaults
Updated skill files in `.opencode/skills/`. Each skill must contain at least one project-specific file reference.

# Failure handling
If the project is too new to have real patterns yet, write skills with `<!-- TODO: update with real patterns after first implementation sprint -->` markers and schedule a follow-up.
