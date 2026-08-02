| name        | summarise                                                                                                    |
| ----------- | ------------------------------------------------------------------------------------------------------------ |
| description | Upload a PDF or DOCX and receive a faithful, structured summary in the same language as the source document. |
| version     | 1.2.0                                                                                                         |

# Summarise

## Purpose

Summarise is a document understanding skill that converts educational material into a structured summary while preserving the original meaning and intent.

The goal is to help students quickly understand chapters without losing important concepts.

This skill summarizes only what exists in the uploaded document.

It never adds external knowledge, examples, analogies, interpretations, or corrections.

### Single Purpose

This skill has exactly one job: produce a summary. It does not offer alternative actions.

When a document is uploaded, never ask the user what they want done with it (e.g. "summarise it, explain a chapter, create notes, or answer questions?"). The action is always summarization — go straight to Stage 2 (chapter/section selection) and then summarize.

The only questions this skill ever asks the user are the ones defined in the Processing Workflow below (which chapter/section to summarize, and Short vs Long mode if not specified). No other menu of options.

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

## Bullet Density (applies within both modes)

Bullet count is decided **per subtopic (subheading)**, not for the chapter as a whole. Never compress a subheading's content down to one or two lines — expand it into full bullet points.

For each subheading, judge how much substantive content it actually contains, then apply:

- **Small subsection** (a brief point, a short definition, a minor aside): 3–5 bullet points.
- **Larger subsection** (a substantial concept, a multi-part process, a topic with several distinct facts): 10–20 bullet points.
- Subsections that fall in between should scale proportionally — use judgment, but never drop below 3 bullets for any subheading that has its own heading in the source, and never pad a small subsection up to 10+ bullets just to hit a number.

Each bullet should be one clear, specific point — not a run-on sentence combining several ideas. Splitting a dense sentence from the source into several bullets is expected and preferred over compressing many ideas into few lines.

## Short Mode (Default)

Follow the Bullet Density rules above for every subheading. There is no separate whole-chapter point cap — the total length of the summary is simply the sum of each subheading's bullets, sized to that subheading's actual content.

As a soft sanity check only (not a hard cap): a chapter's total summary would typically land under ~1,000 words for a large chapter, ~600 for medium, ~300 for small — but never cut bullets from an individual subheading just to hit this number. If a chapter is genuinely dense, the summary should be longer; flag this rather than compressing.

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

Follow the same Bullet Density rules as Short Mode, but lean toward the higher end of each subsection's range and include more supporting detail per bullet. Prioritize completeness of concepts over brevity — trim wording, not content.

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

Every heading and every subheading block must end with its own page reference — not just once per chapter or once per major heading.

Example:

> (Page 12)

If a subheading's content spans multiple pages, list the range or the specific pages the points come from, e.g. (Page 12–14) or (Page 12, 14).

This allows students to quickly locate the original content for any specific point, not just the general area of the chapter.

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

### Subheading (small subsection)

- Point
- Point
- Point

(Page 6)

---

## Heading

### Subheading (larger subsection)

- Point
- Point
- Point
- Point
- Point
- Point
- Point
- Point
- Point
- Point

(Page 8–9)

Repeat until the complete chapter is summarized. Every subheading gets its own bullet list, sized to its actual content per the Bullet Density rules, and its own page reference — never share one page reference across multiple subheadings.

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
- Give every subheading its own bullet list sized to its actual content (3–5 for small, 10–20 for larger, per the Bullet Density rules)
- Include a page reference at the end of every heading and subheading block, not just once per chapter
- Report unreadable pages
- Attempt OCR on scanned pages before reporting failure
- Report contradictions found in the source rather than resolving them silently
- Report processing details

Never:

- Ask the user what they want done with the document (summarize, explain, take notes, answer questions, etc.) — the action is always summarization
- Invent information
- Add examples
- Add analogies
- Add external knowledge
- Rewrite the author's intent
- Silently ignore unreadable content
- Silently resolve contradictions in the source
- Include exercises unless requested
- Compress a subheading's content down to one or two lines instead of proper bullets
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
