---
title: Huang et al. — A Survey on Hallucination in Large Language Models (2023)
type: source
tags: [wiki/source]
date_ingested: 2026-05-19
authors: ["Lei Huang", "Weijiang Yu", "Weitao Ma", "Weihong Zhong (et al.)"]
publisher: ACM Transactions on Information Systems (TOIS)
publication_id: arXiv:2311.05232
year: 2023
url: https://arxiv.org/abs/2311.05232
medium: survey paper
topics: [hallucination, taxonomy, detection, mitigation, RAG]
---

# A Survey on Hallucination in Large Language Models

**Authors:** Lei Huang, Weijiang Yu, Weitao Ma, Weihong Zhong, Zhangyin Feng, Haotian Wang, Qianglong Chen, Weihua Peng, Xiaocheng Feng, Bing Qin, Ting Liu (Harbin Institute of Technology)
**Publisher:** ACM TOIS
**Canonical URL:** <https://arxiv.org/abs/2311.05232>

---

## Summary

The current canonical survey of [[concepts/hallucination|hallucination]] in LLMs. Introduces a taxonomy that distinguishes LLM-era hallucination from prior task-specific NLG hallucination, surveys causes, detection methods, and mitigation strategies, including the limitations of retrieval-augmented generation (RAG) as a fix.

---

## Key Contributions

1. **Updated taxonomy.** Splits hallucination into *factuality* (the claim is wrong about the world) and *faithfulness* (the claim is unsupported by provided source material) — important distinction often conflated.
2. **Causes are multi-layered.** Pre-training data quality, training objective, RLHF artifacts, decoding randomness, and prompting all contribute.
3. **Detection methods.** Token-level uncertainty, consistency checks, retrieval-based verification, model-as-judge — each with trade-offs.
4. **RAG is not a cure.** Even with retrieval, LLMs hallucinate when the retrieved context is irrelevant, contradictory, or absent — and they often fail to abstain when retrieval fails.
5. **Knowledge boundaries.** Models do not reliably know what they do not know (compare with [[sources/kadavath-know-2022|Kadavath et al. 2022]]).

---

## Relevance to This Wiki

- **Primary reference for [[concepts/hallucination|Hallucination]] concept page.**
- **Faithfulness/factuality split** is important for [[synthesis/sat-llm-hypotheses|H7]] design: epistemic labeling can plausibly improve faithfulness (the model knows what it was given) but cannot fully solve factuality (the model doesn't always know what's true).
- **RAG-is-not-a-cure finding** is critical for any agentic system relying on retrieval as a hallucination guard — SATs may still be needed even when sources are provided.

## See Also

- [[sources/kadavath-know-2022|Kadavath et al. — Models Mostly Know What They Know (2022)]] — counterpoint on model self-knowledge
- [[concepts/hallucination|Hallucination]] — concept page
- Ji et al. (2023) *Survey of Hallucination in NLG* (ACM Computing Surveys, [arXiv:2202.03629](https://arxiv.org/abs/2202.03629)) — predecessor survey
