<!--
  seed.md — the DNA of this repository.

  This is the single source of truth and rebuild blueprint. An AI agent can reconstruct the
  ENTIRE repository from this file alone by following the Rebuild Procedure below.

  Sections 1–7 are GENERATED from the live repo state by the `sync-seed` skill on every `/grow`
  tick — do not hand-edit them; they will be overwritten. Only the Evolution Log (section 8) is
  append-only and human/agent-authored via `encode-seed`.
-->

# Repository DNA

## 1. Concept Definition

> Machine-readable. Every generic skill, prompt, and agent reads this block to know what to grow.
> Change the `subject` (and re-derive `taxonomy`) to retarget the entire framework at a new concept.

```yaml
concept:
  subject: "the year 1849"
  scope: "events, people, works, discoveries, and developments occurring in — or directly tied to — the year 1849"
  taxonomy:                 # derived at genesis from the subject; evolvable over time
    - { name: "History & Politics",  slug: history }
    - { name: "Science & Discovery", slug: science }
    - { name: "Arts & Culture",      slug: arts }
    - { name: "Economics",           slug: economics }
    - { name: "People",              slug: people }
  source_strategy: "verify every fact against >=2 authoritative web sources (one encyclopedic, e.g. Wikipedia/Britannica; one specialist where possible)"
  conventions:
    knowledge_table: "README.md > '## Notable Events' table; row = | Event | <=25-word description ending in significance |"
    file_path: "<category-slug>/<topic-slug>.md"      # slug = lowercase, hyphens, no special chars
    frontmatter: [title, date, category]
    tone: "encyclopedic, neutral, factual; active voice; cite sources"
```

## 2. Identity & Mission

This repository is a **self-growing knowledge base** about its `concept.subject` (currently **the
year 1849**). It started from a single prompt and expands autonomously: each growth tick researches
new on-topic content, builds structure (indices, timeline, cross-references), verifies facts, and
publishes — all driven by the Concept Definition above. The framework is **concept-agnostic**:
point it at a different subject and it grows a different knowledge base. 1849 is this instance, not
the framework itself.

## 3. Architecture (customization layer)

Generic, concept-agnostic files in `.github/`. None hardcode 1849 — they read the concept from this
seed.

| File | Type | Purpose |
|------|------|---------|
| `.github/instructions/content.instructions.md` | instructions | Content & format standards; reads concept taxonomy/conventions. Applies to `**/*.md`. |
| `.github/instructions/agents.instructions.md` | instructions | Authoring conventions for `*.agent.md` (tools, sections, delegation). |
| `.github/skills/research/SKILL.md` | skill | Concept-agnostic research: fetch sources, extract facts, verify scope. Writes nothing. |
| `.github/skills/add-topic/SKILL.md` | skill | Research → choose format (row vs file) → create/link → optional log. |
| `.github/skills/build-structure/SKILL.md` | skill | (Re)generate category indices, TIMELINE, TOC/INDEX, cross-refs. Idempotent. |
| `.github/skills/plan-roadmap/SKILL.md` | skill | Read state → score → pick next items → rewrite ROADMAP.md. |
| `.github/skills/sync-seed/SKILL.md` | skill | Regenerate this seed's sections 1–7 from live repo state. |
| `.github/skills/publish-session/SKILL.md` | skill | encode-seed → review → commit → push to main. |
| `.github/agents/curator.agent.md` | agent | Content specialist: research & write per the concept. |
| `.github/agents/architect.agent.md` | agent | Orchestrator: runs one `/grow` tick end-to-end; delegates. |
| `.github/prompts/genesis.prompt.md` | prompt | `/genesis "<concept>"` — bootstrap a fresh autonomous repo for any subject. |
| `.github/prompts/grow.prompt.md` | prompt | `/grow` — run one autonomous growth tick. |
| `.github/prompts/deep-dive.prompt.md` | prompt | Research one topic in depth → dedicated file. |
| `.github/prompts/update-readme.prompt.md` | prompt | Bulk-populate the knowledge table from a topic list / gaps. |
| `.github/prompts/encode-seed.prompt.md` | prompt | Append a session entry to the Evolution Log (section 8). |
| `.github/prompts/publish.prompt.md` | prompt | Thin wrapper over the publish-session skill. |
| `.github/prompts/evolve.prompt.md` | prompt | Audit & improve the customization layer itself. |

## 4. Content Inventory

- **Taxonomy:** see `concept.taxonomy` (History & Politics, Science & Discovery, Arts & Culture, Economics, People).
- **Knowledge table:** `README.md` → `## Notable Events` (15 rows across all five categories as of genesis).
- **Dedicated topic files:** none yet (`<category>/<topic>.md` — to be created by deep-dives).

## 5. Structure Inventory

Generated artifacts (maintained by `build-structure`):
- Category index pages `<category-slug>/index.md` — *not yet generated*.
- `TIMELINE.md` (concept is time-oriented) — *not yet generated*.
- `INDEX.md` / README TOC — *not yet generated*.
- Cross-reference "Related" links between topic files — *not yet generated*.

## 6. Growth Loop

`/grow` runs one tick via the **architect** agent:
1. **Orient** — read this seed, `ROADMAP.md`, `README.md`, repo tree.
2. **Plan** — `plan-roadmap` skill picks the next 1–3 items (content / structure / meta).
3. **Execute** — content → `curator`; structure → `build-structure`; self-improve (periodic) → `evolve`.
4. **Verify** — concept scope + `source_strategy`; no duplicate rows; valid links; required frontmatter.
5. **Record** — update `ROADMAP.md`; `sync-seed` (regenerate sections 1–7); `encode-seed` (append to log).
6. **Publish** — `publish-session` commits and pushes to `main`.

Forward plan / backlog lives in [ROADMAP.md](ROADMAP.md). Run unattended via a Claude scheduled
routine (`/schedule` → `/grow`).

## 7. Rebuild Procedure

To reconstruct this repository from scratch using only this seed:
1. Read the **Concept Definition** (section 1).
2. Run `/genesis "<concept.subject>"` (or recreate the files in section 3 — they are concept-agnostic
   and identical across instances).
3. `genesis` writes this Concept Definition into a fresh `seed.md`, ensures the `.github/` layer
   exists, creates `README.md` framed for the subject with a starter knowledge table, and seeds
   `ROADMAP.md` from the taxonomy.
4. Run `/grow` repeatedly (or via schedule) to regrow content and structure.
Because `sync-seed` keeps sections 1–7 current, this procedure rebuilds whatever state the repo had
reached, not just the original.

---

## 8. Evolution Log

> Append-only history of how this repo was built, in order. Authored via `encode-seed`. Never
> regenerated — this is the genesis record.

## Genesis — plant the 1849 seed — 2026-06-07

Planted this instance from the universal concept-driven framework (the reference 1764 instance),
retargeted to the subject **the year 1849**.

- Derived the Concept Definition for 1849: `subject`, `scope`, a five-part `taxonomy`
  (History & Politics, Science & Discovery, Arts & Culture, Economics, People), `source_strategy`,
  and `conventions` — appropriate to a year-shaped subject.
- Copied the concept-agnostic `.github/` customization layer verbatim (instructions, skills, agents,
  prompts) — none hardcode 1849; they read this seed.
- Wrote `README.md` framed for 1849 with a 15-row, source-verified `## Notable Events` starter table
  spanning all five categories (e.g. the California Gold Rush, Elizabeth Blackwell's medical degree,
  the deaths of Chopin and Poe, the annexation of the Punjab, repeal of the British Navigation Acts).
- Seeded `ROADMAP.md` with an initial backlog derived from the taxonomy (structural artifacts,
  content gaps, an evolve cadence).

Next step: run `/grow` (or register a `/schedule` routine) to produce the first autonomous growth tick.
