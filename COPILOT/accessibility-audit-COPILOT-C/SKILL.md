---
name: accessibility-audit
description: Checks semantic structure, keyboard navigation, contrast ratios, labels, and assistive-technology friendliness. Trigger when auditing a web app for accessibility compliance. Do NOT use for backend or non-UI code reviews.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P1
  maturity: draft
  risk: low
  tags: [accessibility, a11y, WCAG]
---

# Purpose
Audits web applications for accessibility issues including semantic HTML, keyboard navigation, color contrast, ARIA labels, and screen reader compatibility.

# When to use this skill
Use when:
- Auditing a web app for WCAG compliance before launch
- Reviewing UI components for accessibility regressions

Do NOT use when:
- Reviewing backend code with no UI impact
- Doing a general code quality review

# Operating procedure
1. Run an automated audit with axe DevTools or Lighthouse accessibility
2. Verify keyboard-only navigation works for all interactive elements
3. Check color contrast ratios meet WCAG AA (4.5:1 for normal text)
4. Audit ARIA labels and roles for screen reader compatibility
5. Test with a screen reader (NVDA, VoiceOver) for the most critical flows

# Output defaults
An accessibility audit report with automated findings, manual test results, WCAG level ratings, and prioritized fix recommendations.

# Failure handling
If automated tools disagree with manual testing, trust the manual test result. Document the discrepancy for future tooling calibration.
