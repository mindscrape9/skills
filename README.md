# AI Skills

A collection of reusable AI skills designed to automate repetitive workflows and improve the quality of AI responses.

These skills are intentionally lightweight, human-readable, and easy to extend. They focus on giving AI models structured responsibilities rather than writing one-off prompts.

Whether you're studying, programming, creating content, or managing documents, these skills help you achieve more consistent and reliable results.

---

## License

This repository is released under the **MIT License**.

You are free to:

- ✅ Use these skills for personal projects
- ✅ Use them commercially
- ✅ Modify them
- ✅ Share them
- ✅ Build your own skills from them

Attribution is appreciated but not required by the MIT License.

See the [LICENSE](LICENSE) file for full details.

---

# Available Skills

| Skill | Purpose |
|--------|---------|
| summarise | Generate faithful summaries from PDF or DOCX documents while preserving the original meaning. |
| *(More coming soon...)* | |

---

# Philosophy

Every skill in this repository follows a few simple principles:

- Solve one problem well.
- Produce consistent outputs.
- Minimize hallucinations.
- Preserve user intent.
- Prefer structured workflows over large prompts.
- Be easy to read and modify.

---

# How to Use

## ChatGPT

If you're using ChatGPT Skills (or custom prompt workflows):

1. Copy the skill into your preferred skills location.
2. Start a new conversation.
3. Invoke the skill naturally.

Example:

```
@summarise
```

or

```
@summarise detailed
```

Upload your PDF or DOCX and let the skill guide the rest of the workflow.

---

## Claude

Claude supports reusable prompt files and project instructions.

To use these skills:

1. Copy the skill into your Claude Project.
2. Save it as a reusable instruction or prompt.
3. Invoke it naturally during your conversation.

Example:

```
/summarise
```

---

# Example Workflow

```
Upload PDF
        │
        ▼
AI detects document type
        │
        ▼
AI detects chapters
        │
        ▼
Select chapter (if required)
        │
        ▼
Structured summary
        │
        ▼
Processing report
```

---

# Contributing

Contributions are always welcome.

Ideas include:

- New skills
- Workflow improvements
- Better prompts
- Bug fixes
- Documentation improvements
- Performance improvements

If you have an idea that makes a skill more reliable, easier to use, or more maintainable, feel free to open an issue or submit a pull request.

---

# Design Goals

Every skill in this repository should strive to be:

- Reliable
- Reusable
- Maintainable
- Transparent
- Easy to understand
- Easy to extend

---

# Disclaimer

These skills help AI models perform specific workflows more consistently.

Results still depend on:

- the capabilities of the underlying AI model,
- the quality of the uploaded documents,
- and the clarity of the user's request.

Always review AI-generated output before relying on it for academic, professional, legal, or medical purposes.

---

# Roadmap

Planned skills include:

- summarise
- mcq
- flashcards
- revise
- explain
- translate
- compare
- extract
- research
- grill-me
- tdd
- code-review

---

Made with ❤️ for the open-source AI community.
