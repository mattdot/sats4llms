---
title: 'Liu et al. — Lost in the Middle: How Language Models Use Long Contexts (TACL, 2023)'
type: source
tags: [wiki/source]
date_ingested: 2026-05-19
authors: ["Nelson F. Liu (et al.)"]
publisher: Transactions of the Association for Computational Linguistics (TACL)
publication_id: arXiv:2307.03172
year: 2023
url: https://arxiv.org/abs/2307.03172
medium: research paper
topics: [long-context, positional-bias, attention, availability-heuristic, recency, primacy]
---

# Lost in the Middle: How Language Models Use Long Contexts

**Authors:** Nelson F. Liu et al. (Stanford)
**Venue:** TACL 2023
**Canonical URL:** <https://arxiv.org/abs/2307.03172>

---

## Summary

The canonical empirical finding on **LLM positional bias in long contexts**: performance is highest when relevant information appears at the **beginning or end** of the context window, and degrades significantly when the relevant information sits in the middle. Even models explicitly built for long context exhibit this U-shape.

This is the empirical foundation for treating *context recency/primacy weighting* as the LLM analog of the [[concepts/availability-heuristic|Availability Heuristic]]. Information that is structurally "more available" to the model's attention — by virtue of position, not content — exerts disproportionate influence on the output.

---

## Key Findings

1. **U-shape over position.** Performance on multi-document QA and key-value retrieval is highest at the start and end of the context, lowest in the middle.
2. **Holds even for long-context models.** Models advertised as supporting 32k+ tokens still exhibit the U-shape — it is not an artifact of context-window limits.
3. **Holds across task types.** Same pattern for QA and for key-value retrieval — not task-specific.
4. **New evaluation protocols.** Establishes a methodology (positional manipulation) for testing long-context use in any model.

---

## Relevance to This Wiki

- **Empirical foundation for the LLM availability analog.** The "context recency weighting" cell in the Structural Parallel table is *specifically* this finding. It validates that [[concepts/availability-heuristic|Availability Heuristic]] has a real LLM analog that is independently measurable.
- **Critical for [[synthesis/hypotheses/h3-kac-anchoring|H3]] experimental design.** If anchoring is measured in long contexts, position effects from Liu et al. will confound the measurement. Anchoring vs. positional bias must be disentangled.
- **Connects to [[sources/roberts-llm-sats-ftw-2025|Roberts' chunking failure]].** Roberts found KAC breaks across chunks because cross-chunk context is lost. Liu shows *why*: middle-context positional bias means even when context is preserved, mid-context information isn't reliably used.
- **Architectural implication.** Important information should be placed at the start or end of context, not buried in the middle. Pipelines (see [[synthesis/sat-pipeline|SAT Pipeline]]) that pass context across stages should respect this.

## See Also

- [[concepts/availability-heuristic|Availability Heuristic]] — the LLM analog this paper establishes
- [[concepts/key-assumptions-check|Key Assumptions Check]] — KAC interventions need to surface assumptions near the start or end of context to be remembered
- [[synthesis/hypotheses/h3-kac-anchoring|H3]] — must control for positional bias in experimental design
- [[sources/roberts-llm-sats-ftw-2025|Roberts 2025]] — empirical instance of long-document KAC failure that Liu's findings explain
