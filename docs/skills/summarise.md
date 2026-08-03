---
layout: default
title: Summarise
---

# Summarise

**Version:** 1.2.0

Upload a PDF or DOCX and receive a faithful, structured summary in the same language as the source document.

[Download skill folder](https://github.com/mindscrape9/skills/tree/main/skills/summarise) · [SKILL.md on GitHub](https://github.com/mindscrape9/skills/blob/main/skills/summarise/SKILL.md)

---

## What it does

Summarise converts educational documents into structured chapter summaries while preserving the original meaning. It never adds outside knowledge, examples, or corrections.

- Detects chapters and sections automatically
- Follows the document's heading hierarchy
- Adds page references on every section
- Explains difficult words inline
- Reports unreadable or OCR-failed pages

---

## How to use

1. Copy `skills/summarise/` into your AI tool's skills directory.
2. Start a new conversation and invoke `@summarise`.
3. Upload a PDF or DOCX.
4. Select the chapter or section when prompted.
5. Optionally request **long mode** (Short is default).

### Example prompts

```
@summarise
```

```
Summarise chapter 3 in long mode.
```

---

## Options

| Option | Default | Description |
|--------|---------|-------------|
| Summary mode | Short | **Short** — concise, exam-prep friendly. **Long** — fuller detail per subheading. |
| Chapter / section | Prompted | Pick from detected chapters (&lt;10) or specify by name/number (≥10). |
| Language | Same as source | Override only if you ask explicitly. |
| Exercises | Excluded | Included only on request. |
| Diagrams | Educational only | Decorative images are skipped. |

---

## Supported inputs

- **Files:** PDF, DOCX
- **Documents:** Textbooks, lecture notes, study notes, research papers

---

## Output

Each run includes a chapter overview, structured bullet summary with page references, and a processing report (language, pages processed, mode used, any issues).

---

## Workflow

```
Upload → Analyze → Select chapter → Read full chapter → Summarize → Report
```

---

## Install

Copy the entire `skills/summarise/` folder. Your AI tool needs `SKILL.md`; `README.md` is for human reference.

Typical path for Cursor: `~/.cursor/skills/summarise/`

---

[Back to all skills](../)
