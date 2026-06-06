---
name: research-history
description: 'Research and document historical topics for the 1764 repository. Use when: looking up events, people, inventions, or cultural works from the year 1764; crawling Wikipedia or authoritative historical sources; adding new entries to the README or creating dedicated topic files; verifying dates and attribution for 1764-era content.'
argument-hint: 'A topic, person, event, or discovery related to 1764 (e.g. "Sugar Act", "Mozart", "Spinning Jenny")'
---

# Research History (1764)

## What This Skill Does

Given a topic related to the year 1764, this skill:
1. Fetches content from authoritative web sources (Wikipedia, Britannica, etc.)
2. Extracts key facts: date, people involved, context, significance
3. Formats findings as structured markdown
4. Integrates results into the repository (README table or dedicated file)

---

## Procedure

### Step 1 — Identify Sources

For each topic, fetch from the most authoritative sources available:

| Source | URL pattern | Best for |
|--------|------------|---------|
| Wikipedia | `https://en.wikipedia.org/wiki/<Topic>` | Overview, dates, people |
| Britannica | `https://www.britannica.com/search?query=<Topic>+1764` | Verified facts |
| World History Encyclopedia | `https://www.worldhistory.org/search/?q=<Topic>` | Cultural context |

Use the `fetch_webpage` tool with a query like `"<topic> 1764 history events significance"`.

### Step 2 — Extract Key Facts

From fetched content, capture:
- **Date / Period**: Exact date or range within 1764
- **People**: Key figures (name, nationality, role)
- **Event / Work**: What happened or was created
- **Significance**: Why it matters historically
- **Category**: History & Politics / Science & Discovery / Arts & Culture / Economics / People

### Step 3 — Format Output

For README table entries:
```markdown
| <Event Name> | <One-sentence description, ending with significance> |
```

For a dedicated topic file (`./<category>/<topic-slug>.md`):
```markdown
# <Topic Title>

**Date**: 1764  
**Category**: <Category>  
**People**: <Names>

## Summary

<2–3 paragraph overview>

## Key Facts

- <Fact 1>
- <Fact 2>

## Sources

- [Wikipedia](<url>)
- [Britannica](<url>)
```

### Step 4 — Update the Repository

- **Small addition** (single event or person): Add a row to the `Notable Events of 1764` table in [README.md](../../README.md).
- **Deep dive** (multiple related facts or a full topic): Create a new file under the appropriate category folder (e.g., `science/spinning-jenny.md`) and link it from the README.

### Step 5 — Verify

Before saving:
- Confirm all dates fall in or directly relate to 1764
- Check that no duplicate rows exist in the README table
- Ensure sources are publicly accessible (no paywalled URLs)

---

## Example Invocations

```
/research-history Sugar Act
/research-history James Hargreaves Spinning Jenny
/research-history Voltaire Dictionnaire philosophique
/research-history Brown University founding
```

---

## Notes

- If a topic spans multiple years, focus only on what occurred **in 1764** specifically.
- If sources conflict on dates, note the discrepancy and cite both.
- Prefer Wikipedia as the primary crawl target; use Britannica to cross-check.
