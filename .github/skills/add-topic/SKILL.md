---
name: add-topic
description: 'Add one or more 1764 topics to the repository. Use when: adding a new event, person, invention, or cultural work from 1764; unsure whether a topic deserves a README row or a full dedicated article; bulk-adding multiple topics at once; auto-discovering gaps in coverage across the five categories (History & Politics, Science & Discovery, Arts & Culture, Economics, People). Orchestrates research, format selection, file creation, README linking, and session logging.'
argument-hint: 'Topic name or comma-separated list (e.g. "Seven Years War aftermath, Thomas Reid, Gluck opera"). Leave blank to auto-discover coverage gaps.'
---

# Add Topic (1764)

## What This Skill Does

Given one or more topics related to the year 1764, this skill:
1. Researches each topic using authoritative sources
2. Decides the appropriate output format (table row vs. dedicated file)
3. Creates or updates the correct files
4. Links everything from the README
5. Optionally logs the session to `seed.md`

---

## Procedure

### Step 1 — Determine Topics

**If topics were provided as an argument**, use them. Split on commas if multiple.

**If no argument was given**, auto-discover gaps:
- Read [README.md](../../README.md)
- Identify which of the five categories have fewer than 3 entries: History & Politics, Science & Discovery, Arts & Culture, Economics, People
- Propose 1–2 well-known 1764 topics for each under-represented category
- Confirm with the user before proceeding (or proceed with all if running in non-interactive mode)

### Step 2 — Research Each Topic

For each topic, follow the full [research-history](../research-history/SKILL.md) procedure:
- Fetch at least two authoritative sources
- Extract: date/period, key people, what happened, significance, category
- Confirm the topic falls in or directly relates to 1764

If a topic cannot be confirmed as 1764-relevant, skip it and note the reason.

### Step 3 — Choose Output Format

After research, apply this decision rule for each topic:

| Condition | Format |
|-----------|--------|
| Sparse results (1–3 key facts, minor event) | **Table row only** → follow Step 4a |
| Rich results (4+ key facts, notable significance) | **Dedicated file + table row** → follow Step 4b |
| Already has a dedicated file | **Update existing file** and ensure README links it |

When in doubt, prefer the dedicated file — it's always better to have more detail.

### Step 4a — Add a README Table Row

- Open [README.md](../../README.md)
- Add a new row to the `Notable Events of 1764` table:
  ```
  | Event Name | One-sentence description ending with its significance |
  ```
- Do not duplicate existing rows
- Preserve all other content exactly

### Step 4b — Create a Dedicated File + README Link

**Determine file path**: Map the category to the correct folder and slug the name:

| Category | Folder |
|----------|--------|
| History & Politics | `history/` |
| Science & Discovery | `science/` |
| Arts & Culture | `arts/` |
| Economics | `economics/` |
| People | `people/` |

Slug: lowercase, hyphens, no special characters.
Example: `"Thomas Reid"` → `people/thomas-reid.md`

**Create the file** using this template:

```markdown
# <Topic Title>

**Date**: 1764  
**Category**: <Category>  
**People**: <Comma-separated key figures, or "N/A">

## Summary

<2–3 paragraph narrative: what happened, who was involved, why it matters.>

## Key Facts

- <Specific fact, date, or figure>
- <Fact 2>
- <Fact 3>
- <Add more as warranted>

## Historical Significance

<1–2 paragraphs on lasting impact or legacy.>

## Sources

- [Wikipedia](<url>)
- [Britannica or other source](<url>)
```

**Link from README**: Find (or add) the row for this topic in the `Notable Events of 1764` table and turn the Event cell into a link:
```
| [Sugar Act](economics/sugar-act.md) | ... |
```

### Step 5 — Report

After processing all topics, output a summary table:

| Topic | Format | File | Status |
|-------|--------|------|--------|
| Sugar Act | Dedicated file | `economics/sugar-act.md` | Created |
| ... | ... | ... | ... |

Note any topics that were skipped and why.

### Step 6 — Log to Seed (Optional)

If the user asks to record this session, follow the [encode-seed](../../prompts/encode-seed.prompt.md) prompt to append a session entry to [seed.md](../../seed.md).
