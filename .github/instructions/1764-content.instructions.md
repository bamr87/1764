---
description: "Use when adding, editing, or researching topics for the 1764 repository. Covers content standards, source verification, markdown formatting, README table conventions, dedicated topic file structure, and which skills/prompts to invoke. Apply for any historical event, person, invention, or cultural work related to 1764."
applyTo: "**/*.md"
---

# 1764 Repository — Content & Workflow Standards

## Categories

All content belongs to exactly one of these five categories:

| Category | Slug |
|----------|------|
| History & Politics | `history` |
| Science & Discovery | `science` |
| Arts & Culture | `arts` |
| Economics | `economics` |
| People | `people` |

## Source Standards

- Always verify facts from **at least two authoritative sources** (Wikipedia, Britannica, World History Encyclopedia).
- Confirm the topic falls **within or directly connects to the year 1764**. Reject or note topics outside this range.
- Prefer primary-era sources when available (contemporary publications, charter dates, etc.).

## README Table

- Table lives under the `## Notable Events of 1764` heading in [README.md](../../README.md).
- Each row follows this exact format:
  ```
  | Event Name | One-sentence description ending with its significance |
  ```
- Never duplicate an existing row. Check before inserting.
- Keep descriptions factual, neutral in tone, and under 25 words.

## Dedicated Topic Files

Create a dedicated file when research yields **4+ distinct facts** or the topic has notable historical significance.

**Path convention**: `./<category-slug>/<topic-slug>.md` (e.g., `arts/voltaire-dictionnaire-philosophique.md`)

**Required front-matter and structure**:
```markdown
---
title: "<Topic Title>"
date: 1764
category: "<Category>"
---

# <Topic Title>

**Date**: <exact date or "1764">  
**Category**: <Category>  
**People**: <Key figures>

## Summary

<2–3 paragraph overview of the event, work, or person>

## Significance

<Why this matters — impact on the era or on history>

## Sources

- [<Source Title>](<URL>)
```

- If a dedicated file exists, always link its filename in the README table row:
  ```
  | [Event Name](arts/topic-slug.md) | Description |
  ```

## Agent Workflow

### Adding a new topic
Use the **add-topic** skill. It handles research → format decision → file creation → README linking → optional seed logging.

### Researching a topic only
Use the **research-history** skill. Returns structured facts; does not write files unless instructed.

### Bulk-populating the README
Use the **update-readme** prompt (`/update-readme`). Accepts a topic list or auto-detects category gaps.

### Creating a long-form article
Use the **deep-dive** prompt (`/deep-dive`). Produces a full dedicated topic file with citations.

### Logging a session
Use the **encode-seed** prompt (`/encode-seed`) to append a structured entry to `seed.md` at the end of a working session.

## Content Tone & Style

- Write in **clear, formal prose** appropriate for an encyclopedic reference.
- Use **active voice** and present tense for descriptions, past tense for narrative sections.
- Avoid editorializing. State facts and significance without personal opinion.
- Spell out numbers under ten; use numerals for years, dates, quantities over nine.
- Use British English spellings for era-appropriate proper nouns (e.g., *Encyclopédie*); American English otherwise.
