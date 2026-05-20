---
title: Du et al. — Improving Factuality and Reasoning in Language Models through Multiagent Debate (2023)
type: source
tags: [wiki/source]
date_ingested: 2026-05-19
authors: ["[[entities/yilun-du|Yilun Du]] (et al.)"]
publisher: arXiv preprint (MIT)
publication_id: arXiv:2305.14325
year: 2023
url: https://arxiv.org/abs/2305.14325
medium: research paper
topics: [multi-agent, debate, groupthink, factuality, reasoning, society-of-minds]
---

# Improving Factuality and Reasoning in Language Models through Multiagent Debate

**Authors:** Yilun Du, Shuang Li, Antonio Torralba, Joshua B. Tenenbaum, Igor Mordatch
**Affiliation:** MIT / Google Brain
**Canonical URL:** <https://arxiv.org/abs/2305.14325>
**Project page:** <https://composable-models.github.io/llm_debate/>

---

## Summary

The foundational paper on **multi-agent debate** as an LLM reasoning protocol. Multiple instances of a language model propose answers and then *critique each other's reasoning* over multiple rounds before converging on a final answer. This significantly improves mathematical and strategic reasoning, and **reduces hallucinations and factual errors** compared to single-agent generation.

Direct empirical evidence for [[synthesis/sat-llm-hypotheses|H5]] (multi-agent SAT pipelines outperform single-agent chains). The mechanism Du et al. describe is structurally identical to the [[concepts/groupthink|groupthink]]-control argument.

---

## Key Findings

1. **Multi-round debate improves factuality.** Reduces wrong answers across math, reasoning, and factual QA benchmarks.
2. **Debate reduces hallucination.** Multiple instances catch and correct each other's confabulated content.
3. **Black-box compatible.** Works with closed API models without fine-tuning.
4. **Uniform across tasks.** Same procedure and prompts work across diverse evaluation tasks.
5. **"Society of minds" framing.** Reframes LLM reasoning as a collaborative process rather than a single forward pass.

---

## Important Caveat (Per This Wiki's Critique)

Du et al.'s "multiple instances" share the **same base model**. From a [[concepts/groupthink|groupthink]] perspective, this is like polling identical analysts — they share priors, biases, and failure modes. The improvement Du et al. measure may come more from the *iterative-critique* structure than from genuine epistemic independence.

This is exactly the caveat raised in [[synthesis/sat-llm-hypotheses|H5]]: a true test of multi-agent SAT pipelines would compare same-model debate vs. *different-model* debate to isolate the structure-vs-independence contribution.

---

## Relevance to This Wiki

- **Direct partial validation of [[synthesis/sat-llm-hypotheses|H5]].** Confirms multi-agent debate improves output quality; does not yet isolate which component matters.
- **Empirical support for [[concepts/groupthink|Groupthink]] countermeasures in LLM contexts.**
- **Architectural pattern for [[synthesis/sat-pipeline|SAT Pipeline]] Pattern B (parallel + adversarial).**
- **Methodological precedent.** Multi-round, multi-instance protocols are tractable to evaluate and improve performance.

## See Also

- [[concepts/groupthink|Groupthink]]
- [[concepts/devils-advocacy|Devil's Advocacy]] — structurally similar single-agent technique
- [[concepts/team-a-team-b|Team A/Team B]] — the SAT equivalent of debate
- [[synthesis/sat-llm-hypotheses|H5]] — hypothesis page
- Liang et al. (2023) *Encouraging Divergent Thinking in LLMs through Multi-Agent Debate* ([arXiv:2305.19118](https://arxiv.org/abs/2305.19118)) — follow-up
