---
name: migration-pack-builder
description: "Generates retrofit plans, replacement lists, and managed-surface migration artifacts for existing repos. Important when upgrading already-evolving projects rather than greenfield repos. Trigger when the task context clearly involves migration pack builder."
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
  tags: [migration, retrofit, upgrade]
---

# Purpose
Build a structured migration plan that transforms "we need to upgrade X" into an inventory of affected code, risk-ranked migration sequence, concrete rollback procedures, and acceptance criteria. This turns chaotic upgrade projects into methodical execution.

# When to use this skill
Use when:
- Major dependency upgrade (e.g., React 17→18, Python 3.9→3.12, Django 3→4)
- Framework migration (e.g., Express→Fastify, Create React App→Vite)
- Infrastructure migration (e.g., Heroku→AWS, self-hosted→managed service)
- "Modernize the codebase" initiative without clear scope

Do NOT use when:
- Patch-level dependency updates (use dependency-upgrades skill)
- Greenfield projects (no migration needed)
- Single-file changes that don't warrant a plan

# Operating procedure
1. **Create migration inventory**:
   ```markdown
   ## Inventory: [Migration Name]
   
   ### Direct Dependencies
   | Package | Current | Target | Breaking Changes |
   |---------|---------|--------|------------------|
   | react   | 17.0.2  | 18.2.0 | Concurrent mode, useId |
   
   ### Affected Files
   - src/components/*.tsx (147 files) - JSX transform changes
   - src/hooks/*.ts (23 files) - useEffect cleanup timing
   
   ### Integration Points
   - CI/CD: Node version requirement changes
   - Testing: @testing-library/react upgrade required
   ```

2. **Risk assessment per component**:
   - **High risk**: Core business logic, payment flows, auth, data persistence
   - **Medium risk**: UI components, utilities with many dependents
   - **Low risk**: Dev tooling, test utilities, isolated features
   
3. **Define migration sequence** (dependency order + risk mitigation):
   ```markdown
   ### Migration Sequence
   1. [ ] Update build tooling (low risk, unblocks others)
   2. [ ] Migrate test utilities (enables validation)
   3. [ ] Low-risk leaf components (build confidence)
   4. [ ] Core utilities (high dependency count)
   5. [ ] High-risk business logic (with extra validation)
   ```

4. **Rollback procedure per stage**:
   ```markdown
   ### Rollback: Stage 3 (Leaf Components)
   - Git: `git revert HEAD~5..HEAD` (5 commits)
   - Dependencies: `npm ci` from lockfile at tag `pre-stage-3`
   - Verification: Run `npm test && npm run e2e`
   ```

5. **Acceptance criteria**:
   ```markdown
   ### Acceptance Criteria
   - [ ] All existing tests pass without modification (or intentional updates documented)
   - [ ] No TypeScript errors introduced
   - [ ] Bundle size delta < 5%
   - [ ] Lighthouse performance score maintained
   - [ ] Manual QA of critical user flows: login, checkout, data export
   ```

# Output defaults
```markdown
# Migration Pack: [Name] - [From] → [To]

## Summary
- **Scope**: [number] files, [number] packages
- **Estimated effort**: [X] days
- **Risk level**: [High/Medium/Low]

## Inventory
[inventory table]

## Migration Sequence
[ordered stages with checkboxes]

## Rollback Procedures
[per-stage rollback instructions]

## Acceptance Criteria
[checklist]

## Known Issues & Workarounds
[documented blockers and their solutions]
```

# References
- https://martinfowler.com/articles/enterprisePatterns.html (migration patterns)

# Failure handling
- **Circular dependencies in migration order**: Identify the cycle; often requires splitting a component or creating a compatibility shim
- **No test coverage for affected code**: Add characterization tests BEFORE migration to capture current behavior
- **Breaking change not documented upstream**: Check GitHub issues, migration guides, and changelogs; document your findings
- **Partial migration state blocks progress**: Always use feature branches with atomic commits; never merge partial migration to main
