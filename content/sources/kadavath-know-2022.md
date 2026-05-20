---
title: Kadavath et al. — Language Models (Mostly) Know What They Know (2022)
type: source
tags: [wiki/source]
date_ingested: 2026-05-19
authors: ["[[entities/saurav-kadavath|Saurav Kadavath]] (et al.)"]
publisher: arXiv preprint (Anthropic)
publication_id: arXiv:2207.05221
year: 2022
url: https://arxiv.org/abs/2207.05221
medium: research paper
topics: [calibration, self-knowledge, introspection, hallucination, uncertainty]
---

# Language Models (Mostly) Know What They Know

**Authors:** Saurav Kadavath, Tom Conerly, Amanda Askell, Tom Henighan, Dawn Drain, Ethan Perez, Nicholas Schiefer et al.
**Affiliation:** [[entities/anthropic|Anthropic]]
**Canonical URL:** <https://arxiv.org/abs/2207.05221>

---

## Summary

A foundational result on LLM self-knowledge: large models can be **trained or prompted to predict whether their own answers are correct**, with calibration that improves with scale. Models that produce wrong answers often "know" the answer is uncertain — the information is *present in the activations* but not always *expressed in the output*.

This reframes [[concepts/hallucination|hallucination]] from a *knowledge* problem to a *generation* problem. The model knows it doesn't know; the autoregressive sampling process doesn't surface that uncertainty.

---

## Key Findings

1. **Self-evaluation is well-calibrated.** When asked "is your answer correct?" the model's probability of "yes" correlates well with actual accuracy, especially at larger scales.
2. **P(True) is meaningful.** Specifically training a separate "P(True)" head produces well-calibrated probability scores that the model's last answer was correct.
3. **Scale helps.** Self-knowledge improves with model size — another inverse-scaling result *avoided* (this one improves rather than worsens with scale).
4. **Self-knowledge generalizes.** Models can predict correctness on tasks they weren't trained to self-evaluate on.

---

## Relevance to This Wiki

- **Direct empirical foundation for [[synthesis/sat-llm-hypotheses|H7]] (epistemic labeling reduces hallucination).** Kadavath shows the information needed for accurate uncertainty labeling *exists* in the model. Whether structured SAT-style labeling can extract it reliably is the open H7 question.
- **Critical caveat for [[concepts/hallucination|Hallucination]].** Hallucination is not pure ignorance — it is failure to surface uncertainty that the model already represents internally. SATs that force uncertainty expression have a plausible mechanism to work.
- **Supports [[concepts/overconfidence-bias|Overconfidence Bias]] mapping.** Models default to confident expression even when their internal P(True) is low — exactly the human overconfidence pattern.

## See Also

- [[sources/tian-calibration-2023|Tian et al. — Just Ask for Calibration (2023)]] — practical recovery of calibration on RLHF'd models
- [[sources/huang-hallucination-survey-2023|Huang et al. — Hallucination Survey (2023)]]
- [[concepts/hallucination|Hallucination]], [[concepts/overconfidence-bias|Overconfidence Bias]]
