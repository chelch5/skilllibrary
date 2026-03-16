---
name: forms-validation
description: Handles form structure, client-side validation, error display, and submission behavior in web apps. Trigger when building or reviewing forms. Do NOT use for backend input sanitization.
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
  tags: [forms, validation, UX]
---

# Purpose
Provides patterns for well-structured forms with clear validation, accessible error messages, and reliable submission behavior.

# When to use this skill
Use when:
- Building a form with user input that needs validation before submission
- Reviewing form UX for accessibility and error handling quality

Do NOT use when:
- Implementing backend input sanitization or API-level validation
- Building read-only data displays

# Operating procedure
1. Define the form schema with required fields and validation rules (use Zod or react-hook-form)
2. Show inline validation errors on field blur, not just on submit
3. Disable the submit button during submission; show a loading state
4. Handle server-side errors by mapping them to form fields where possible
5. Ensure all form elements have accessible labels and ARIA attributes

# Output defaults
A form component with schema-validated fields, accessible error messages, and submission state handling.

# Failure handling
If the backend returns an unexpected error format, display a generic user-friendly message. Log the raw error for debugging.
