# Summarise

**Version:** 1.2.0

Upload a PDF or DOCX and receive a faithful, structured summary in the same language as the source document.

Summarise is built for students and learners who need to understand textbook chapters, lecture notes, and research papers quickly — without losing meaning or introducing outside information.

---

## What it does

- Reads PDF and DOCX educational documents
- Detects chapters and sections automatically
- Produces structured summaries that follow the original document hierarchy
- Preserves the author's intent — no added examples, analogies, or corrections
- Includes page references so you can jump back to the source
- Explains difficult words inline on first use
- Reports what could not be read (including failed OCR on scanned pages)

---

## Installation

MindScrape skills are plain markdown files. Copy the skill folder into whatever location your AI tool uses for reusable instructions or skills.

1. Download or clone this repository.
2. Copy the `skills/summarise/` folder to your skills directory.
3. Ensure your tool loads `SKILL.md` as the agent instruction file.

Typical locations (adjust for your setup):

| Tool type | Common path |
|-----------|-------------|
| Cursor | `~/.cursor/skills/summarise/` |
| Custom prompt library | Your project's prompts or instructions folder |

You only need `SKILL.md` for the agent to run the skill. This `README.md` is for human reference.

---

## How to use

1. Start a new conversation with your AI assistant.
2. Invoke the skill by name (e.g. `@summarise` or paste the skill instructions).
3. Upload a PDF or DOCX file.
4. When prompted, choose which chapter or section to summarize.
5. Optionally specify **Short** or **Long** mode (Short is the default).
6. Review the structured summary and Processing Report.

### Example prompts

```
@summarise
```

```
Summarise chapter 3 from the uploaded textbook in long mode.
```

```
@summarise — short summary of the Introduction section
```

---

## Options

| Option | Default | Description |
|--------|---------|-------------|
| **Summary mode** | Short | **Short** — concise bullets sized to each subheading. **Long** — more detail, higher bullet counts, fuller concept coverage. |
| **Chapter / section** | Prompted | If the document has fewer than 10 chapters, you pick from a detected list. If 10 or more, you specify the chapter number or name. Documents without chapters use major sections instead. |
| **Language** | Same as source | Summary is written in the document's language. Request another language explicitly if needed. |
| **Exercises** | Excluded | Questions, activities, and assignments are skipped unless you ask to include them. |
| **Diagrams** | Educational only | Diagrams that aid understanding are explained; decorative images are ignored. |

### Summary modes in detail

**Short mode (default)**

- Bullet count scales per subheading (3–5 for small sections, 10–20 for larger ones)
- Best for quick review before class or exams
- Soft word-count guidance: ~300 words (small chapter), ~600 (medium), ~1,000 (large)

**Long mode**

- Same structure as Short mode, but more bullets and supporting detail per subheading
- Best when you need fuller coverage of definitions, processes, and diagram explanations
- Prioritizes completeness over brevity

---

## Supported inputs

| Type | Formats |
|------|---------|
| Files | PDF, DOCX |
| Documents | Textbooks, lecture notes, study notes, research papers, educational PDFs |

Scanned pages without text are handled via OCR when possible. Unreadable pages are reported, not guessed.

---

## Output

Each run produces:

1. **Chapter title** and estimated reading time
2. **Chapter overview** — high-level summary of what the chapter covers
3. **Structured sections** — headings, subheadings, bullet points, and page references
4. **Processing report** — language, pages processed, OCR recovery, mode used, and any issues

---

## Workflow

```
Upload PDF or DOCX
        │
        ▼
Document analysis (type, language, pages, structure)
        │
        ▼
Select chapter or section
        │
        ▼
Read full chapter (not section-by-section)
        │
        ▼
Generate summary (Short or Long mode)
        │
        ▼
Processing report
```

---

## Principles

- **Faithful** — only content from the uploaded document
- **Structured** — mirrors chapter → heading → subheading hierarchy
- **Traceable** — page references on every heading block
- **Transparent** — contradictions and unreadable pages are reported, not hidden

---

## Limitations

Results depend on the AI model, document quality, and scan/OCR accuracy. Always review output before relying on it for academic, professional, legal, or medical purposes.

---

## Files in this folder

| File | Purpose |
|------|---------|
| `SKILL.md` | Agent instructions — copy this into your AI tool |
| `README.md` | Human documentation (this file) |
