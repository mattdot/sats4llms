---
type: log
tags: [wiki/log]
---

# Wiki Operations Log

Append-only. Format: `## [YYYY-MM-DD] operation | Title`

---

## [2026-05-20] ingest | suprathermal — ACH-Grounding (GitHub, 2024)

User-supplied source: open-source Python implementation of ACH as an LLM grounding mechanism. https://github.com/suprathermal/ACH-Grounding

Created:
- `sources/suprathermal-ach-grounding-2024.md` — full source summary
- `entities/suprathermal.md` — author entity

Updated:
- `concepts/analysis-of-competing-hypotheses.md` — added "ACH as RAG Grounding" section documenting the matrix-cell-only LLM design + classical synthesis pattern; bumped source_count 2→4 (Roberts + suprathermal both cite this concept now); added source row
- `synthesis/hypotheses/h1-ach-confirmation-bias.md` — added evidence row for suprathermal; added paragraph on architecture refinement (test the cell-level form, not single-prompt)

Key finding: **Two independent implementations (Roberts 2025, suprathermal 2024) converge on the same architecture** — multi-step LLM calls + externalized synthesis. suprathermal goes further by delegating *all* combinatorial reasoning to classical algorithms, citing provable hallucination bounds (arXiv:2401.11817). This is meaningful empirical evidence for H1's design: ACH-as-pipeline works, ACH-as-prompt fails.

---

## [2026-05-19] ingest | Grey Dynamics — Intelligence Failure (2024)

User-supplied source on intelligence failure as a multi-stage phenomenon. Two distinct contributions to the wiki:

- Real-world case studies — Iraq WMD (2003) and Russia/Ukraine (2022) — grounding the abstract bias library in documented consequential events
- The **Intelligence Cycle** as a 5-stage process framework (Direction → Collection → Processing → Analysis → Dissemination) that maps cleanly onto LLM agentic pipelines

**Created:**
- `sources/grey-dynamics-intelligence-failure-2024.md` — full source summary with case studies, biases catalog, key quotes, LLM relevance
- `entities/grey-dynamics.md` — publisher entity
- `concepts/intelligence-cycle.md` — process framework concept; includes 5-stage table mapped to LLM agentic pipeline analogs and per-stage LLM failure modes

**Note:** Article mentions "Proportionality Bias" which is outside the wiki's current 12-bias scope; not ingested as a concept page per prior scope decision.

Pages touched: 4

---

## [2026-05-19] expand | Fill in Structural Parallel research backing

User noted the Structural Parallel table on the homepage had many unlinked cells — Premature Closure had no concept page, and the LLM Equivalents column was largely descriptive prose with no supporting research linked. Filled the gaps:

**New concept pages:**
- `concepts/premature-closure.md` — distinct human bias (also called satisficing per Heuer/RAND). Covers LLM manifestation (single-hypothesis generation, CoT rationalization, greedy decoding), with empirical evidence from Roberts and Echterhoff.
- `concepts/persona-capture.md` — LLM-native failure mode (third in the LLM-native bias group with sycophancy and hallucination). Covers manifestations including persona-driven jailbreaks, cross-cultural simulation distortion, role-locked agentic systems.

**New source pages:**
- `sources/shanahan-roleplay-2023.md` — Murray Shanahan et al. *Role play with large language models* (Nature 2023). Theoretical foundation for persona capture.
- `sources/liu-lost-in-middle-2023.md` — Nelson Liu et al. *Lost in the Middle* (TACL 2023). Canonical evidence for context positional bias as the LLM analog of availability heuristic.
- `sources/casper-rlhf-2023.md` — Stephen Casper et al. *Open Problems and Fundamental Limitations of RLHF* (2023). Theoretical foundation for RLHF reward-following as the LLM analog of motivated reasoning.

**Homepage Structural Parallel table updated:** every cell now wikilinked. The LLM Equivalents column now includes inline source citations (e.g., "Persona capture (Shanahan 2023, Durmus 2023)") so the research backing is visible at a glance.

Catalog: 15 sources, 32 concepts. Stats updated.

Pages touched: 8

---

## [2026-05-19] add | Bias Evaluations methodology page + soften homepage overclaim

User feedback: bullet #3 on the homepage ("Implementation is now proven, not theoretical") overstated where the field actually is. Roberts and Du are early signal, not proof. Also: the idea of evaluations — building judges that detect bias as a failure mode in a reasoning trace — deserves its own page since it's the operational bridge from "hypothesis claim" to "actual experiment."

- Created `synthesis/bias-evals.md` — methodology for bias judges. Covers: what a judge looks like per bias, three implementation modes (LLM, human, hybrid), methodology principles (process not outcome, counterfactual framing, multi-turn for sycophancy, different-model judges, pre-registration, calibration), per-hypothesis judge mapping, and what's new vs. existing eval literature.
- Updated homepage bullet #3: now leads with "We can measure it" framing — evals + judges as what makes the thesis testable. Roberts and Du framed as "existence proofs in practice, not proof in general."
- Added "I want to measure whether a bias actually impaired my flow" item to homepage "In Practice" section pointing to bias-evals
- Updated catalog Synthesis Pages table (13 total)
- Pages touched: 4


Parse latest entries: `grep "^## \[" Wiki/log.md | tail -5`

---

## [2026-05-19] scaffold | Wiki initialized

- Created `Wiki/` directory structure: sources/, entities/, concepts/, synthesis/
- Created `Wiki/index.md`, `Wiki/log.md`, `Wiki/overview.md`
- Configured `assets/` as attachment folder in `.obsidian/app.json`
- Bound Ctrl+Shift+D hotkey for downloading attachments in `.obsidian/hotkeys.json`
- Created `Clippings/` directory for raw sources
- Added LLM Wiki schema to `CLAUDE.md`
- Vault has no raw sources yet — ready for calibration once sources are added

---

## [2026-05-19] ingest | A Tradecraft Primer (CIA, 2009)

- Source: `Clippings/Tradecraft-Primer-apr09.pdf` (downloaded from CIA website; 45 pages)
- Created `Wiki/sources/tradecraft-primer-2009.md`
- Created entities: `richards-j-heuer-jr.md`, `center-for-the-study-of-intelligence.md`, `sherman-kent-center.md`
- Created concepts: `structured-analytic-techniques.md`, `cognitive-bias.md`, `mind-set.md`, `key-assumptions-check.md`, `quality-of-information-check.md`, `indicators-or-signposts-of-change.md`, `analysis-of-competing-hypotheses.md`, `devils-advocacy.md`, `team-a-team-b.md`, `high-impact-low-probability-analysis.md`, `what-if-analysis.md`, `brainstorming.md`, `outside-in-thinking.md`, `red-team-analysis.md`, `alternative-futures-analysis.md`
- Updated `Wiki/index.md`, `Wiki/overview.md`
- Pages touched: 18

---

## [2026-05-19] ingest | SATs: Explanation and Relevance (Shawn Riley, LinkedIn)

- Source: https://www.linkedin.com/pulse/structured-analytic-techniques-sats-explanation-relevance-shawn-riley-fglec/
- Created `Wiki/sources/riley-sats-cybersecurity-2024.md`
- Created entity: `shawn-riley.md`
- Created concept: `confirmation-bias.md`
- Updated existing concept pages to add cybersecurity application sections and second source citations: `key-assumptions-check.md`, `analysis-of-competing-hypotheses.md`, `devils-advocacy.md`, `red-team-analysis.md`, `brainstorming.md`, `what-if-analysis.md`, `high-impact-low-probability-analysis.md`, `indicators-or-signposts-of-change.md`, `outside-in-thinking.md`, `alternative-futures-analysis.md`, `cognitive-bias.md`, `structured-analytic-techniques.md`
- Updated `Wiki/index.md`, `Wiki/overview.md`
- Pages touched: 15
- Note: RAND RR1408 (third requested source) inaccessible — 403 error from rand.org

---

## [2026-05-19] ingest | RAND RR1408 — Assessing the Value of SATs in the U.S. IC (Artner, Girven & Bruce, 2016)

- Source URL: https://www.rand.org/pubs/research_reports/RR1408.html (previously blocked; user provided downloaded PDF)
- Created `sources/rand-rr1408-2016.md` — full source summary including pilot study findings, empirical literature review, proposed evaluation methodology
- Created entities: `stephen-artner.md`, `richard-girven.md`, `james-bruce.md`, `rand-corporation.md`, `odni.md`
- Replaced the three "blocked" references in `catalog.md`, `index.md`, `log.md` with working links to the canonical RAND URL
- Updated catalog Sources and Entities tables; updated Stats (4 sources, 16 entities)
- Key empirical findings now in wiki:
  - Mitre 2004 — ACH reduces confirmation bias only for non-professional analysts
  - Nemeth 2001 — formal devil's advocacy may heighten confidence in preferred hypotheses
  - Tetlock 2005 — scenarios reduced prediction accuracy in two experiments
  - Folker 2000 — structured hypothesis testing improved accuracy in 1 of 2 experiments
- Key conceptual contribution: face validity vs. empirical validity distinction; Treverton typology (puzzles/mysteries/complexities); ICD 203 standards
- Pages touched: 8

---

## [2026-05-19] ingest | Eight LLM-bias empirical papers

Following user request to ingest existing LLM-bias research rather than just cite it inline. Ingested as full source pages per CLAUDE.md schema, with author/institution entities and concept-page citations.

**New source pages (8):**
- `sources/sharma-sycophancy-2023.md` — Sharma et al. (Anthropic) on RLHF-induced sycophancy
- `sources/perez-mwe-2022.md` — Perez et al. (Anthropic) model-written evals; sycophancy increases with scale + RLHF
- `sources/huang-hallucination-survey-2023.md` — Huang et al. canonical hallucination survey (ACM TOIS); faithfulness vs factuality split
- `sources/kadavath-know-2022.md` — Kadavath et al. (Anthropic) on LLM self-knowledge; P(True) is well-calibrated at scale
- `sources/tian-calibration-2023.md` — Tian et al. (Stanford, EMNLP 2023) verbalized confidence recovers calibration
- `sources/du-debate-2023.md` — Du et al. (MIT) multi-agent debate improves factuality/reasoning
- `sources/durmus-global-opinions-2023.md` — Durmus et al. (Anthropic) GlobalOpinionQA, WEIRD bias quantified
- `sources/echterhoff-biasbuster-2024.md` — Echterhoff et al. BiasBuster: anchoring, framing, availability, confirmation in LLMs

**New entity pages (8):** Anthropic, Mrinank Sharma, Ethan Perez, Saurav Kadavath, Esin Durmus, Katherine Tian, Yilun Du, Jessica Echterhoff

**Concept pages updated with Empirical Evidence (LLM) sections (12):**
- Sycophancy (Sharma, Perez)
- Hallucination (Huang, Kadavath)
- Overconfidence Bias (Tian, Kadavath)
- Mirror Imaging (Durmus)
- Groupthink (Du)
- Anchoring Bias, Framing Effect, Availability Heuristic, Confirmation Bias (Echterhoff)
- Motivated Reasoning, Hindsight Bias, Status Quo Bias — gap notes added (no direct LLM studies)

**Synthesis updated:**
- `synthesis/sat-llm-hypotheses.md` — added "Empirical Status Summary" table mapping each of H0-H7 to current evidence
- Sources_used frontmatter updated to include all 11 sources

**Catalog updated:** Sources table (+8), Entities table (+8), Stats (12 sources / 24 entities)

Pages touched: 30

---

## [2026-05-19] restructure | Split each hypothesis into its own page

Per user request — each H# now has its own dedicated page in `synthesis/hypotheses/`. The parent `synthesis/sat-llm-hypotheses.md` is now a framework page holding H0 (meta), the empirical-status overview table linking to all 7 children, and the cross-cutting experimental design principles.

- Created `synthesis/hypotheses/h1-ach-confirmation-bias.md`
- Created `synthesis/hypotheses/h2-devils-advocacy-sycophancy.md`
- Created `synthesis/hypotheses/h3-kac-anchoring.md`
- Created `synthesis/hypotheses/h4-red-team-mirror-imaging.md`
- Created `synthesis/hypotheses/h5-multi-agent-groupthink.md`
- Created `synthesis/hypotheses/h6-what-if-overconfidence.md`
- Created `synthesis/hypotheses/h7-epistemic-labeling-hallucination.md`
- Each child page has its own Empirical Evidence section with the relevant citations
- Slimmed parent page significantly; replaced anchor-based table links with whole-page links
- Updated homepage H1–H7 table to link to children, not anchors
- Updated catalog Synthesis Pages table

Pages touched: 11

---

## [2026-05-19] expand | Bias reference pages + LLM synthesis

- Created 9 individual bias concept pages with full academic references and LLM agentic systems context:
  `anchoring-bias.md` · `availability-heuristic.md` · `groupthink.md` · `overconfidence-bias.md` · `mirror-imaging.md` · `motivated-reasoning.md` · `framing-effect.md` · `hindsight-bias.md` · `status-quo-bias.md`
- Expanded `confirmation-bias.md` with full references (Wason 1960, Nickerson 1998)
- Updated `cognitive-bias.md` as a hub page with full bias library tables mapping biases to SATs
- Added "Biases Primarily Controlled" table to all 12 SAT technique pages
- Created `Wiki/synthesis/sats-for-llm-agents.md` — LLM bias taxonomy, SAT adaptations as prompt patterns, architectural patterns
- Created `Wiki/synthesis/bias-sat-matrix.md` — full cross-reference matrix (SAT→biases, biases→SATs, LLM coverage)
- Updated `Wiki/index.md`
- Pages touched: 27

---

## [2026-05-19] ingest | LLM SATs FTW (Scott Roberts, sroberts.io)

- Source: https://sroberts.io/posts/llm-sats-ftw/ (SANS Emerging Threats Summit 2025 companion post)
- Created `Clippings/roberts-llm-sats-ftw-2025.md` (raw clipping, immutable)
- Created `Wiki/sources/roberts-llm-sats-ftw-2025.md`
- Created entities: `scott-roberts.md`, `randolph-h-pherson.md`, `sans-emerging-threats-summit.md`, `heuer-pherson-book.md`
- Created concept: `starbursting.md` (new SAT — Idea Generation; from Heuer/Pherson book, not CIA Primer)
- Updated `analysis-of-competing-hypotheses.md` — LLM Implementation section; multi-step sequential pattern confirmed; single-prompt anti-pattern warned
- Updated `key-assumptions-check.md` — LLM Implementation section; cross-chunk context loss failure mode documented
- Updated `structured-analytic-techniques.md` — Heuer/Pherson additional techniques section added; source_count → 3
- Updated `sats-for-llm-agents.md` — corrected ACH to multi-step; KAC chunk failure mode; Starbursting SAT #8; Empirical Evidence section; updated open questions
- Updated `Wiki/index.md`
- Key finding: Roberts is first empirical source — confirms SAT-LLM patterns; identifies failure modes
- Pages touched: 10

---

## [2026-05-19] expand | Gap fill — theoretical foundations + LLM-native biases + synthesis

- Created `Wiki/concepts/sycophancy.md` — LLM-native bias; RLHF artifact; confirmation bias + groupthink combined; includes prompt patterns for adversarial prompting and pressure-testing
- Created `Wiki/concepts/hallucination.md` — LLM-native failure mode; no internal uncertainty signal; maps to overconfidence; includes epistemic labeling and source grounding prompt patterns
- Created `Wiki/concepts/system-1-system-2.md` — Kahneman/Tversky dual-process framework; theoretical root explaining why biases exist and why SATs work; includes LLM functional analog table
- Created `Wiki/entities/daniel-kahneman.md` — heuristics-and-biases program co-founder; Nobel laureate; *Thinking, Fast and Slow*
- Created `Wiki/entities/amos-tversky.md` — Kahneman's research partner; prospect theory, framing effects, availability heuristic
- Created `Wiki/entities/irving-janis.md` — groupthink research originator (1972); Bay of Pigs, Pearl Harbor case studies
- Created `Wiki/synthesis/sat-selection-guide.md` — decision guide: given problem type or bias risk, which SAT to apply; organized by process stage, bias risk, and problem type; minimum viable intervention table
- Created `Wiki/synthesis/sat-pipeline.md` — full pipeline (Scoping→Analysis→Challenge→Forecast); minimal 3-step pipeline; Pattern A (sequential single-agent), Pattern B (parallel independent + adversarial), Pattern C (post-hoc audit); pipeline failure modes; System 1/2 framing
- Updated `Wiki/concepts/cognitive-bias.md` — added System 1/2 reference as theoretical root; added LLM-native failure modes table (Sycophancy, Hallucination)
- Updated `Wiki/synthesis/sats-for-llm-agents.md` — linked Sycophancy and Hallucination concept pages; updated See Also
- Updated `Wiki/index.md`, `Wiki/log.md`
- Pages touched: 11

---

## [2026-05-19] synthesize | Testable Hypotheses: SATs + LLM Quality

- Created `Wiki/synthesis/sat-llm-hypotheses.md`
- H0 (meta): structural compliance ≠ debiasing — must falsify first; semantic distance test
- H1: ACH reduces confirmation bias — ground truth comparison on known-outcome cases
- H2: Devil's Advocacy suppresses sycophancy under multi-turn pushback — position stability test
- H3: KAC prevents anchoring propagation — framing independence test
- H4: Red Team improves adversarial robustness — expert blind rating
- H5: Multi-agent pipelines outperform single-agent chains — genuine independence test
- H6: What If? reduces overconfidence — confidence calibration measurement
- H7: Epistemic labeling reduces hallucination rate — verifiable claims against source documents
- Includes experimental design principles: ground truth problem, blind rating vs. LLM-as-judge, per-hypothesis quality operationalization, Roberts anti-pattern warning
- Updated `Wiki/index.md`, `Wiki/log.md`
- Pages touched: 3
