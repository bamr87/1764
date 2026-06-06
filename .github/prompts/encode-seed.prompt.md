---
name: Encode into Seed
description: "Append the current session's actions to seed.md as a reproducible log. Use when: recording what was just built or changed; documenting tool calls, file creations, and decisions made this session; maintaining a genesis log so the repo can be re-seeded from scratch."
argument-hint: "Optional: a short label for this session entry (e.g. 'Add research-history skill'). Defaults to today's date and a summary."
agent: agent
tools: [read_file, replace_string_in_file]
---

Append a new session entry to [seed.md](../seed.md) that records what was done in this conversation.

## Instructions

### 1. Gather what happened this session

Review the conversation history and collect:
- **Tools run**: name of each tool called, its key inputs, and its output/result
- **Files created or modified**: paths and a one-line description of the change
- **Decisions made**: any branching logic or choices (e.g., "chose workspace scope over user scope")
- **Session label**: use the argument if provided; otherwise derive a short label from the primary action (e.g., "Add research-history skill and update-readme prompt")

### 2. Format the entry

Use this structure:

```
---

## <Session Label> — <YYYY-MM-DD>

<1–2 sentence summary of what was accomplished.>

<For each significant tool call:>
Ran <Tool Name>
Completed with input: {
  <key inputs as JSON>
}

<outcome or result in plain English>

<For each file created/modified:>
- Created/Updated `<path>`: <one-line description>
```

### 3. Append to seed.md

- Read the current contents of [seed.md](../seed.md).
- Append the new entry at the **bottom** of the file, separated by a blank line.
- Do **not** modify any existing content.

### 4. Confirm

Report what was appended: the session label, date, number of tool calls recorded, and files listed.
