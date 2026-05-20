---
title: Echterhoff et al. — Cognitive Bias in Decision-Making with LLMs (BiasBuster, 2024)
type: source
tags: [wiki/source]
date_ingested: 2026-05-19
authors: ["[[entities/jessica-echterhoff|Jessica Maria Echterhoff]] (et al.)"]
publisher: arXiv preprint (UC San Diego)
publication_id: arXiv:2403.00811
year: 2024
url: https://arxiv.org/abs/2403.00811
medium: research paper
topics: [cognitive-bias, anchoring, framing, availability, confirmation, debiasing, decision-making]
---

# Cognitive Bias in Decision-Making with Large Language Models (BiasBuster)

**Authors:** Jessica Maria Echterhoff et al. (UC San Diego)
**Canonical URL:** <https://arxiv.org/abs/2403.00811>

---

## Summary

The most comprehensive single empirical study testing **multiple cognitive biases simultaneously** in LLM decision-making. Introduces **BiasBuster**, a framework + dataset of **13,465 prompts** designed to probe specific cognitive biases in LLMs, evaluate mitigation strategies, and propose a self-debiasing approach.

This is the closest existing work to the empirical program proposed in [[synthesis/sat-llm-hypotheses|the wiki's hypotheses page]].

---

## Biases Tested (All Already Covered in This Wiki)

The paper organizes biases into three categories. The categories that map to wiki concept pages:

| BiasBuster category | Wiki concept page |
|---|---|
| Prompt-induced (e.g. anchoring via primed numbers) | [[concepts/anchoring-bias\|Anchoring Bias]] |
| Sequential (e.g. order effects) | [[concepts/availability-heuristic\|Availability Heuristic]] / [[concepts/anchoring-bias\|Anchoring]] |
| Inherent (e.g. framing-driven response shifts) | [[concepts/framing-effect\|Framing Effect]] |
| Confirmation-style probing | [[concepts/confirmation-bias\|Confirmation Bias]] |

---

## Key Findings

1. **Cognitive bias is present across commercial and open-source models.** Not just a small-model or unaligned-model phenomenon — present in GPT-4-class systems.
2. **Effect sizes vary by bias.** Anchoring and framing show strong effects; some others are subtler.
3. **Self-debiasing works.** A novel method asking LLMs to identify and counter their own bias in prompts is effective, without requiring per-bias manually-crafted examples.
4. **Mitigation transfers.** A single self-debiasing prompt strategy reduces multiple bias types — a kind of [[concepts/key-assumptions-check|Key Assumptions Check]] applied to the model's own reasoning.

---

## Relevance to This Wiki

This paper is **the single best empirical reference** for the LLM versions of:

- [[concepts/anchoring-bias|Anchoring Bias]] — direct measurement
- [[concepts/framing-effect|Framing Effect]] — direct measurement
- [[concepts/availability-heuristic|Availability Heuristic]] — via sequential / recency effects
- [[concepts/confirmation-bias|Confirmation Bias]] — direct measurement

It is also **partial empirical support for [[synthesis/sat-llm-hypotheses|H3]] (KAC prevents anchoring propagation)**. The self-debiasing prompt Echterhoff proposes is functionally a KAC variant — "what assumptions are baked into this prompt?" — applied to bias rather than to evidence.

**Open question raised:** Echterhoff's mitigation works on isolated decisions. Whether the same approach holds up in multi-turn agentic chains (where bias propagates across context) is untested.

## See Also

- [[concepts/anchoring-bias|Anchoring Bias]]
- [[concepts/framing-effect|Framing Effect]]
- [[concepts/availability-heuristic|Availability Heuristic]]
- [[concepts/confirmation-bias|Confirmation Bias]]
- [[concepts/key-assumptions-check|Key Assumptions Check]]
- [[synthesis/sat-llm-hypotheses|Testable Hypotheses]] — H1, H3
- Suri et al. (2024) *Do Large Language Models Show Decision Heuristics Similar to Humans?* — adjacent study
- Tjuatja et al. (2024) *Do LLMs Exhibit Human-like Response Biases?* — survey-context companion
