---
title: Durmus et al. — Towards Measuring the Representation of Subjective Global Opinions in Language Models (2023)
type: source
tags: [wiki/source]
date_ingested: 2026-05-19
authors: ["[[entities/esin-durmus|Esin Durmus]] (et al.)"]
publisher: arXiv preprint (Anthropic)
publication_id: arXiv:2306.16388
year: 2023
url: https://arxiv.org/abs/2306.16388
medium: research paper
topics: [cultural-bias, mirror-imaging, opinions, alignment, WEIRD]
---

# Towards Measuring the Representation of Subjective Global Opinions in Language Models

**Authors:** Esin Durmus, Karina Nguyen, Thomas I. Liao, Nicholas Schiefer et al.
**Affiliation:** [[entities/anthropic|Anthropic]]
**Canonical URL:** <https://arxiv.org/abs/2306.16388>

---

## Summary

A quantitative framework for measuring **whose opinions an LLM's responses are more similar to**. The authors build **GlobalOpinionQA** from cross-national surveys (Pew, World Values Survey) and measure similarity between LLM responses and human responses per country.

**Headline finding:** by default, LLM responses are most similar to the opinions of certain populations — primarily the USA, parts of Europe, and parts of South America. This is a direct quantification of [[concepts/mirror-imaging|mirror imaging]] at the cultural / values level.

---

## Key Findings

1. **Default LLM opinions are WEIRD-biased.** Responses align most with Western, Educated, Industrialized, Rich, Democratic populations — primarily USA opinions.
2. **Country-conditioning helps but distorts.** When prompted to consider a specific country's perspective, the model shifts — but introduces stereotypes and may caricature the target population.
3. **Translation does not fix it.** Translating into the language of the target country does not meaningfully shift opinion alignment toward that country.
4. **Implications for agentic systems modeling foreign actors.** An LLM agent asked to model an adversary's reasoning will, by default, model a USA-flavored adversary.

---

## Relevance to This Wiki

- **Direct empirical foundation for [[concepts/mirror-imaging|Mirror Imaging]] as an LLM phenomenon.** Quantifies what was previously a qualitative claim.
- **Critical for [[synthesis/sat-llm-hypotheses|H4]] (Red Team produces adversarially robust plans).** If a red-teaming LLM has WEIRD priors and can't reliably shift them via country-prompting, its adversarial modeling will be biased toward Western threat archetypes. This is a specific failure mode for H4 testing.
- **Caution for [[concepts/red-team-analysis|Red Team Analysis]] in LLM contexts.** Persona prompting works but unevenly; check that adversary models aren't sanitized versions of Western actors.
- **Caution for [[concepts/outside-in-thinking|Outside-In Thinking]].** "Considering external context" is undermined if the model's default external context is also WEIRD.

## See Also

- [[concepts/mirror-imaging|Mirror Imaging]]
- [[concepts/red-team-analysis|Red Team Analysis]]
- Atari et al. (2023) *Which Humans?* — the WEIRD critique
- Cao et al. (2023) *Assessing cross-cultural alignment between ChatGPT and human societies*
