---
type: log
tags: [wiki/log]
---

# Wiki Operations Log

Append-only. Format: `## [YYYY-MM-DD] operation | Title`

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
