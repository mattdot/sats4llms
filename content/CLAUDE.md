# CLAUDE.md — Agent Instructions for This Vault

This file governs how the LLM agent (Claude, Codex, or any tool-using model) interacts with this Obsidian vault. Read it at the start of every session.

---

## LLM Wiki

This vault implements the **llm-wiki pattern** based on [Karpathy's design](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) — using LLMs to incrementally build and maintain a persistent, interlinked wiki from raw sources rather than re-deriving knowledge on every query. Implementation guide: https://gist.github.com/kennyg/6c45cace2e1c4e424a28fcd51dd6c25b

---

### Architecture

Three layers:

1. **Raw sources** (`Clippings/`) — immutable clippings and captures. Read only, never modify.
2. **The wiki** (`Wiki/`) — LLM-generated, interlinked markdown. You own this entirely.
3. **The schema** (`CLAUDE.md`) — these instructions. Tells you how to maintain the wiki.

---

### Wiki Directory Structure

```
Wiki/
├── index.md          # content catalog — read this FIRST on every operation
├── log.md            # append-only operation log
├── overview.md       # high-level synthesis of everything
├── sources/          # one summary page per ingested raw source
├── entities/         # people, tools, orgs, repos
├── concepts/         # ideas, patterns, techniques
└── synthesis/        # query answers filed back into wiki
```

Supporting directories:
- `Clippings/` — raw source files (immutable)
- `assets/` — downloaded images (attachment folder)

---

### Page Conventions

Every wiki page **must** have:

```yaml
---
type: <source-summary | entity | concept | synthesis>
tags: [wiki/<type>]
date_updated: YYYY-MM-DD
---
```

Additional frontmatter by type:

**source-summary:**
```yaml
source_file: "[[Clippings/filename]]"
source_date: YYYY-MM-DD        # publication date if known
author: "Name"
topics: [topic1, topic2]
```

**entity:**
```yaml
entity_type: <person | tool | org | repo | other>
source_count: N
```

**concept:**
```yaml
confidence: <high | medium | low>
source_count: N
```

**synthesis:**
```yaml
query: "the question that prompted this synthesis"
sources_used: ["[[Wiki/sources/X]]", "[[Wiki/sources/Y]]"]
```

Style rules:
- Use `[[wikilinks]]` with display text — every mention of a known entity or concept gets a wikilink
  - Format: `[[Wiki/section/slug|Human Readable Name]]` — e.g., `[[Wiki/concepts/confirmation-bias|Confirmation Bias]]`
  - **Slug must be kebab-case matching the actual filename** — `confirmation-bias` not `Confirmation Bias` or `Confirmation bias`
  - Always include the display text after `|` so links read naturally in both edit and preview mode
  - Never use bare `[[Wiki/concepts/slug]]` without a display name
  - **Inside table cells**, use `\|` instead of `|`: `[[Wiki/concepts/confirmation-bias\|Confirmation Bias]]` — a plain `|` breaks the table column separator
- **Never use `[key::value]` inline fields in page bodies** — Obsidian renders them as broken links. All metadata goes in YAML frontmatter only.
- Use `---` section separators for readability
- Keep sentences in source summaries factual and attributable
- Interpretation and analysis belongs in concept or synthesis pages, not source summaries

---

### Operations

#### INGEST — Process a raw source into the wiki

Steps (always in this order):
1. Read the raw source completely
2. Create `Wiki/sources/<slug>.md` — factual summary, key quotes, all entities and concepts mentioned as wikilinks
3. Create or update `Wiki/entities/<name>.md` for each person, tool, org, or repo mentioned
4. Create or update `Wiki/concepts/<name>.md` for each idea or pattern
5. Update `Wiki/index.md` — add row to Sources table, add/update Entities and Concepts tables, remove from Unprocessed Sources list, update Stats
6. Update `Wiki/overview.md` if the big picture changed
7. Append to `Wiki/log.md`: `## [YYYY-MM-DD] ingest | <Source Title>`

A single ingest typically touches 5–15 wiki pages.

**Contradiction rule:** If a new source contradicts an existing wiki page, add a `## Contradictions` section to the relevant concept or entity page noting the disagreement with citations. Never silently overwrite.

#### QUERY — Answer a question from the wiki

Steps:
1. Read `Wiki/index.md` to identify relevant pages
2. Read relevant wiki pages (prefer wiki over raw sources — the wiki should have what you need)
3. Synthesize an answer with wikilinks to supporting pages
4. If the answer is substantial, file it as `Wiki/synthesis/<slug>.md`
5. If synthesis page was created: update `Wiki/index.md` and append to `Wiki/log.md`

#### LINT — Health-check the wiki

Check for:
- Orphan pages (no inbound links)
- Broken wikilinks (link target doesn't exist)
- Stale pages (`date_updated` older than the newest source touching that concept)
- Contradictions between pages
- Concepts mentioned in prose but lacking their own page
- Missing cross-references (entity X mentioned in 5 pages but only linked in 2)
- Sources in `Clippings/` not in the Unprocessed or ingested list

Report findings as a checklist. File result as `Wiki/synthesis/lint-YYYY-MM-DD.md` and update index + log.

---

### Absolute Rules

1. **Never modify files in `Clippings/`** — they are immutable raw sources
2. **Always update `Wiki/index.md` and `Wiki/log.md`** on every wiki change, no exceptions
3. **Source summaries are factual** — no interpretation, no editorializing
4. **Contradictions are surfaced explicitly** — never silently overwrite
5. **Every wiki page gets `type:` frontmatter and `wiki/*` tags**
6. **Use `[[Wiki/section/slug|Display Name]]` for every mention** of an entity or concept that has a wiki page — always include the display name after `|`

---

### Obsidian Setup (Windows)

**Attachment folder:** Configured in `.obsidian/app.json` → `"attachmentFolderPath": "assets/"`. After clipping an article, press **Ctrl+Shift+D** to download remote images to `assets/`.

**Obsidian CLI:** Not yet in PATH. To enable (Obsidian 1.12+ required):
1. In Obsidian: Settings → General → Command line interface → Register CLI
2. Add `%LOCALAPPDATA%\Obsidian\` (or wherever `obsidian.exe` lives) to your Windows PATH
3. Verify: `obsidian help`

**qmd search:** Not installed (requires Go). To install when Go is available:
```
go install github.com/tobi/qmd@latest
qmd collection add sats C:\work\sats\SATs "**/*.md"
qmd update && qmd embed
qmd context add qmd://sats/ "Obsidian vault with LLM wiki and raw source clippings"
qmd context add qmd://sats/Wiki "LLM-generated wiki: source summaries, entities, concepts, synthesis"
```
At small scale, `Wiki/index.md` is sufficient for navigation.

---

### Recommended Plugins

- **Dataview** — SQL-like queries over frontmatter (`type:`, `source_count:`, `confidence:`, etc.)
- **Obsidian Web Clipper** — browser extension to clip articles to `Clippings/` as markdown
- **Graph View** (core) — visualize wiki shape, hubs, orphans, clusters
- **Tasks** — track ingest tasks or lint findings as checkboxes
