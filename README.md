# SATs for LLMs

**Structured Analytic Techniques for Large Language Model–based Agentic Systems**

📖 **Live site: <https://mattdot.github.io/sats4llms/>**

---

## What this is

A working wiki exploring how **Structured Analytic Techniques (SATs)** — the disciplined reasoning methods developed by the US intelligence community to combat cognitive bias in human analysts — can be adapted into architectural patterns and prompt protocols for **LLM-based agentic systems**.

LLMs exhibit systematic biases that are structurally analogous to the cognitive biases SATs were designed to counteract. Because LLM agents are software systems, these interventions can be implemented as deterministic protocols — not just advisory guidelines.

> SATs don't make LLMs smarter. They make the reasoning process more adversarial toward its own conclusions.

## What's in here

The wiki currently contains:

- **3 ingested primary sources** — CIA's *Tradecraft Primer* (2009), Shawn Riley's "SATs in Cybersecurity" (2024), Scott Roberts' "LLM SATs FTW" (2025)
- **13 SAT technique pages** — ACH, Key Assumptions Check, Devil's Advocacy, Red Team, What If?, Starbursting, and more
- **12 cognitive bias pages** — anchoring, confirmation, groupthink, mirror imaging, motivated reasoning, etc., each with LLM analog mappings
- **2 LLM-native failure mode pages** — sycophancy and hallucination, with prompt-pattern countermeasures
- **5 synthesis pages**:
  - *SATs for LLM Agents* — the core case mapping each SAT to an LLM failure mode
  - *Bias × SAT Matrix* — full cross-reference
  - *SAT Selection Guide* — given a problem type or bias risk, which SAT to apply
  - *SAT Pipeline* — how SATs compose into a complete agentic workflow
  - *Testable Hypotheses* — experimental designs to verify the SAT-LLM thesis

## Project structure

```
sats4llms/
├── content/
│   └── Wiki/              # The actual wiki (Quartz content root)
│       ├── concepts/      # SATs and biases
│       ├── entities/      # People, orgs, books
│       ├── sources/       # Ingested source summaries
│       ├── synthesis/     # Cross-source analysis pages
│       ├── index.md       # Catalog (homepage)
│       ├── log.md         # Operations log
│       └── overview.md    # Thesis & wiki structure
├── CLAUDE.md              # Schema for AI agents maintaining the wiki
├── quartz.config.ts       # Static site config
└── .github/workflows/
    └── deploy.yml         # Build & deploy to GitHub Pages
```

## How it's built

The wiki is authored as an [Obsidian](https://obsidian.md) vault and published as a static site with [Quartz v4](https://quartz.jzhao.xyz/). Pushes to `main` trigger a GitHub Actions workflow that builds the site and deploys it to GitHub Pages.

To preview locally:

```bash
npm ci
npx quartz build --directory content/Wiki --serve
```

Then open <http://localhost:8080>.

## Conventions

- **Sources are immutable.** Raw ingested content is preserved verbatim. Interpretation lives only in synthesis pages.
- **Heavy use of `[[wikilinks]]`** so the Obsidian graph view and Quartz cross-references both work.
- **Every page has `type:` in frontmatter** and a `wiki/*` tag — `source`, `entity`, `concept`, `synthesis`, `index`, or `log`.
- **Synthesis pages cite their sources** in `sources_used:` frontmatter and inline.
- **Confidence is explicit** — `high`, `medium`, `low` — based on source convergence.

See [`CLAUDE.md`](./CLAUDE.md) for the full schema followed by both human and AI contributors.

## Contributing

Issues and PRs welcome, especially:

- Additional primary sources (academic papers on SAT effectiveness, more LLM-bias empirical studies)
- Counter-evidence — cases where SAT-style structure did *not* improve LLM output
- Implementations of the patterns described in [SATs for LLM Agents](https://mattdot.github.io/sats4llms/synthesis/sats-for-llm-agents)

## License

Content is original synthesis. Quoted excerpts from sources are used under fair use with attribution. Source material remains under its original license.
