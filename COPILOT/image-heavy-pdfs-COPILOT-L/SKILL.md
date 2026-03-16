---
name: image-heavy-pdfs
description: Specializes PDF handling when content is primarily diagrams, screenshots, or images rather than selectable text. Use for scanned documents or image-based PDFs.
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
  tags: [pdf, ocr, images, extraction]
---

# Purpose
Specializes PDF handling when content is primarily diagrams, screenshots, or images rather than selectable text.

# When to use this skill
Use when:
- Extracting content from scanned or image-based PDFs
- Running OCR on PDFs with non-selectable text
- Processing PDFs where diagrams carry key information

Do NOT use when:
- Text-based PDFs with selectable content (use pdf-extraction)
- Simple image transformations (use image-editor)

# Operating procedure
1. Detect image-heavy vs text-based PDF pages
2. Apply OCR engine (Tesseract, AWS Textract, Azure Vision)
3. Extract and describe visual diagram content
4. Combine OCR text with image context
5. Flag low-confidence OCR regions for human review

# Output defaults
Extracted text with OCR confidence scores, image descriptions, and page references

# Failure handling
If OCR accuracy is low (<85%), escalate to human review. Document confidence thresholds.
