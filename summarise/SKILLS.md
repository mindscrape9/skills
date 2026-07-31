| name        | summarise                                                                                                    |
| ----------- | ------------------------------------------------------------------------------------------------------------ |
| description | Upload a PDF or DOCX and receive a faithful, structured summary in the same language as the source document. |
| version     | 1.1.0                                                                                                         |

# Summarise

## Purpose

Summarise is a document understanding skill that converts educational material into a structured summary while preserving the original meaning and intent.

The goal is to help students quickly understand chapters without losing important concepts.

This skill summarizes only what exists in the uploaded document.

It never adds external knowledge, examples, analogies, interpretations, or corrections.

---

# Supported Files

- PDF
- DOCX

---

# Supported Documents

- Textbooks
- Lecture Notes
- Study Notes
- Research Papers
- Educational Documents

---

# Core Principles

## 1. Faithful Summary

Summarise only information present in the uploaded document.

Never:

- Add outside knowledge
- Add examples
- Add analogies
- Add explanations not found in the source
- Correct the textbook
- Replace the author's intent

If information does not exist in the document, do not include it.

### Handling Contradictions

If the source document contradicts itself across pages or sections (e.g. two different definitions of the same term, conflicting figures):

- Report both versions exactly as written.
- Note the page number for each.
- Do not decide which version is "correct" and do not silently pick one.

Example:

> Note: The document defines "inflation" differently on Page 4 and Page 19. Both definitions are shown below.

---

## 2. Preserve Meaning

Simplify wording while preserving meaning.

Never oversimplify important concepts.

The summary should reduce reading time without reducing understanding.

---

## 3. Preserve Document Structure

Always preserve the original structure.

Follow:

Chapter
↓
Heading
↓
Subheading
↓
Summary

Merge only extremely small or repetitive subheadings.

Never merge major sections.

---

## 4. Never Skip Information

Never silently ignore content.

If something cannot be processed, report it.

Example:

> Page 18 could not be read.

### Scanned / Image-Only Pages

If a page or document contains no extractable text (e.g. a scanned image with no OCR layer):

- Attempt OCR on the page.
- If OCR succeeds, summarize the recovered text as normal and note that it was OCR-extracted.
- If OCR fails or produces unreliable output, do not guess the content. Report it instead:

> Page 22 is a scanned image and could not be reliably read (OCR failed).

---

## 5. Same Language Output

Generate the summary in the same language as the uploaded document.

Only use another language if the user explicitly requests it.

### Mixed-Language Documents

If a document switches languages mid-document (e.g. a textbook in English with quoted passages in another language):

- Use the dominant language of the chapter for the summary.
- Keep short quoted foreign-language terms or titles as-is, with a brief inline translation in parentheses if it aids understanding.
- Note in the Processing Report if a chapter contains mixed languages.

---

# Processing Workflow

Follow these steps exactly.

## Stage 1 — Document Analysis

Determine:

- Document type
- Language(s) present
- Number of pages
- Number of chapters
- Number of major headings
- Number of diagrams

Do not generate the summary yet.

---

## Stage 2 — Structure Detection

If document contains chapters:

If chapters < 10

Show detected chapters and ask the user which chapter to summarize.

If chapters ≥ 10

Ask the user to specify the chapter.

If no chapters exist:

Detect major sections and present them for selection.

---

## Stage 3 — Chapter Understanding

Before summarizing:

Read the complete selected chapter.

Do not summarize section-by-section while reading.

Understand the complete chapter first.

Then generate the summary.

---

## Stage 4 — Generate Summary

Generate either:

Short Mode

or

Long Mode

---

# Summary Modes

## Short Mode (Default)

Adaptive summary.

Small chapter:

Approximately 5 key points. Target under 300 words.

Medium chapter:

Approximately 8–12 key points. Target under 600 words.

Large chapter:

Approximately 10–20 key points. Target under 1,000 words.

If a chapter is unusually long and would exceed these limits even at the low end of the point range, prioritize the most important concepts and note that the summary has been condensed further than usual.

Always preserve the chapter's core message.

---

## Long Mode

More detailed summary.

Preserve:

- Major headings
- Major subheadings
- Important definitions
- Important concepts
- Important processes
- Diagram explanations

Merge only repetitive content.

Target a soft ceiling of roughly double the Short Mode word count for the same chapter. If exceeding this, prioritize completeness of concepts over completeness of prose (trim wording, not content).

---

# Diagram Handling

Explain diagrams only if they contribute to understanding the chapter.

Ignore:

- Decorative images
- Author photos
- Page artwork
- Non-educational graphics

---

# Exercises

Ignore:

- Exercises
- Questions
- Activities
- Projects
- Assignments

Unless the user explicitly requests them.

---

# Difficult Words

Whenever a difficult word appears for the first time:

Explain it inline.

Example:

> Photosynthesis (The process by which plants make food using sunlight.)

Do not generate a separate glossary.

---

# Page References

Always include page references.

Example:

> (Page 12)

This allows students to quickly locate the original content.

---

# Output Format

# Chapter Title

Estimated Reading Time

---

# Chapter Overview

Provide a concise overview explaining what the chapter is about.

Do not introduce external information.

---

## Heading

### Subheading

- Point
- Point
- Point

(Page 6)

---

## Heading

### Subheading

- Point
- Point

(Page 8)

Repeat until the complete chapter is summarized.

---

# Processing Report

Language:

Document Type:

Pages Processed:

Unreadable Pages:

OCR Pages Recovered:

Diagrams Explained:

Exercises Included:

Page References:

Summary Mode:

Mixed Language Detected:

---

# Worked Example

**Input (excerpt from a source chapter, Page 6):**

> "Cellular respiration is the process by which cells break down glucose to release energy. This occurs in the mitochondria and produces ATP, carbon dioxide, and water as byproducts. The process has three main stages: glycolysis, the Krebs cycle, and the electron transport chain."

**Expected Output:**

```
## Cellular Respiration

### Overview of the Process

- Cellular respiration breaks down glucose to release energy for the cell
- Occurs in the mitochondria (Mitochondria: the organelle responsible for producing most of a cell's energy.)
- Produces ATP, carbon dioxide, and water as byproducts
- Has three main stages: glycolysis, the Krebs cycle, and the electron transport chain

(Page 6)
```

This example calibrates tone (plain but precise), structure (heading → bullets → page reference), and inline difficult-word handling (mitochondria) for a single passage. Use it as a reference for density and phrasing, not as content to copy.

---

# Behaviour Rules

Always:

- Detect language(s)
- Detect document type
- Detect headings
- Detect subheadings
- Detect diagrams
- Detect difficult words
- Preserve author's intent
- Preserve document hierarchy
- Include page references
- Report unreadable pages
- Attempt OCR on scanned pages before reporting failure
- Report contradictions found in the source rather than resolving them silently
- Report processing details

Never:

- Invent information
- Add examples
- Add analogies
- Add external knowledge
- Rewrite the author's intent
- Silently ignore unreadable content
- Silently resolve contradictions in the source
- Include exercises unless requested
- Exceed the word-count targets without flagging that the summary was condensed

---

# Success Criteria

A successful summary should allow a student to:

- Understand the chapter without reading every paragraph.
- Locate the original source using page references.
- Trust that no external information has been introduced.
- Know if any content could not be processed, including scanned pages that failed OCR.
- Know if the source document contained contradictions or mixed languages.
- Read the summary significantly faster than the original chapter while retaining the chapter's key ideas.
