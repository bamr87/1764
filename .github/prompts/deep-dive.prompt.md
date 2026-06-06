---
name: Deep Dive a 1764 Topic
description: "Research a single 1764 topic in depth and create a dedicated markdown file for it. Use when: exploring a specific event, person, invention, or cultural work from 1764 in detail; creating a standalone article beyond what fits in a README table row; building out the category folders (history/, science/, arts/, economics/, people/)."
argument-hint: "A topic from 1764 to explore in depth (e.g. 'Sugar Act', 'Voltaire Dictionnaire philosophique', 'Mozart London visit')"
agent: agent
tools: [fetch_webpage, read_file, create_file, replace_string_in_file]
---

Research the provided topic in depth and produce a dedicated markdown file for it in the [1764 repository](../../README.md).

## Instructions

### 1. Load the research skill

Read and follow [research-history](../skills/research-history/SKILL.md) for all research steps (source identification, fact extraction, and date verification).

### 2. Determine the topic

- Use the argument provided by the user.
- If no argument was given, read [README.md](../../README.md) and pick the most notable event in the table that does not yet have a dedicated file.

### 3. Research the topic

Execute the full `research-history` procedure:
- Fetch at least two authoritative sources (Wikipedia, Britannica, World History Encyclopedia).
- Extract: date/period, key people, what happened, historical significance, and category.
- Confirm the topic falls in or directly relates to 1764.

### 4. Determine the file path

Map the topic's category to a folder:

| Category | Folder |
|----------|--------|
| History & Politics | `history/` |
| Science & Discovery | `science/` |
| Arts & Culture | `arts/` |
| Economics | `economics/` |
| People | `people/` |

Slug the topic name (lowercase, hyphens, no special characters).
Example: "Sugar Act" → `economics/sugar-act.md`

### 5. Create the topic file

Use this template:

```markdown
# <Topic Title>

**Date**: 1764  
**Category**: <Category>  
**People**: <Comma-separated key figures, or "N/A">

## Summary

<2–3 paragraph narrative covering what happened, who was involved, and why it matters.>

## Key Facts

- <Fact 1 — specific detail, date, or figure>
- <Fact 2>
- <Fact 3>
- <Add more as warranted>

## Historical Significance

<1–2 paragraphs on the lasting impact or legacy of this event/person/work.>

## Sources

- [Wikipedia](<url>)
- [Britannica or other source](<url>)
```

### 6. Link from the README

- Open [README.md](../../README.md).
- Find the row for this topic in the `Notable Events of 1764` table (add one if it doesn't exist).
- Append a markdown link to the new file in that row's Event cell.
  - Example: `| [Sugar Act](economics/sugar-act.md) | ... |`
- Preserve all other content exactly.

### 7. Report

Summarize:
- The file created (path)
- Top 3 most interesting facts found
- Whether a README link was added or updated
