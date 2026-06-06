---
name: Update README with Research
description: "Populate or expand the 1764 README by researching topics with the research-history skill. Use when: adding new events, people, or discoveries to the Notable Events table; bulk-updating the README from a list of topics; enriching existing entries with better descriptions."
argument-hint: "Comma-separated topics to research and add (e.g. 'Sugar Act, Mozart, Spinning Jenny'). Leave blank to suggest missing topics automatically."
agent: agent
tools: [fetch_webpage, read_file, replace_string_in_file, multi_replace_string_in_file]
---

Research and update [README.md](../README.md) using the `research-history` skill.

## Instructions

1. **Load the skill**: Read and follow [research-history](../skills/research-history/SKILL.md) for all research steps.

2. **Determine topics**:
   - If topics were provided as arguments, use those.
   - Otherwise, read the current [README.md](../README.md) and identify gaps — categories (History & Politics, Science & Discovery, Arts & Culture, Economics, People) that have fewer than 2 entries, or well-known 1764 events not yet listed.

3. **Research each topic**: For each topic, execute the full `research-history` procedure (fetch sources, extract facts, verify the date is 1764).

4. **Update the README**:
   - Add a new row to the `Notable Events of 1764` table for each researched topic.
   - Format: `| Event Name | One-sentence description ending with its significance |`
   - Do **not** duplicate existing rows.
   - Preserve all existing content exactly.

5. **Report**: After updating, list the topics added and any that were skipped (e.g., couldn't confirm 1764 date or source was inaccessible).
