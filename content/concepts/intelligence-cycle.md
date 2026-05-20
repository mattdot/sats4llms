---
title: Intelligence Cycle
type: concept
tags: [wiki/concept, framework, process]
date_updated: 2026-05-19
confidence: high
source_count: 2
domain: intelligence-tradecraft
also_called: ["intelligence process", "intelligence production cycle"]
---

# The Intelligence Cycle

A canonical five-stage framework describing how intelligence is produced, from consumer question to analytic product delivered to decision-makers. Foundational to intelligence tradecraft education. Failure can originate at any stage — and failures at one stage compound downstream.

The cycle is the closest structural parallel in the intelligence-analysis literature to an **LLM agentic pipeline**, which makes it a useful framing device for the wiki's central thesis. Each stage has direct LLM analogs and corresponding LLM-specific failure modes.

---

## The Five Stages

| # | Stage | What happens | Common failure modes |
|---|---|---|---|
| 1 | **Direction** | Consumer sets the intelligence question / requirement | Narrow framing; ambiguous question; mismatched scope |
| 2 | **Collection** | Information is gathered from sources (HUMINT, SIGINT, IMINT, OSINT) | Single-source dependence; collection-strategy gaps; source-bias |
| 3 | **Processing** | Raw collection is validated, translated, structured | Filtering errors; mis-translation; misclassification |
| 4 | **Analysis** | Analysts extract insight, evaluate hypotheses, form judgments | Cognitive bias (see [[concepts/cognitive-bias\|Cognitive Bias]]); mind-set lock-in; [[concepts/premature-closure\|premature closure]] |
| 5 | **Dissemination** | Finished intelligence is communicated to decision-makers | Policymaker rejection of accurate intel; format inappropriate to consumer; over-confident language |

---

## LLM Agentic Pipeline Parallel

The five-stage cycle maps remarkably cleanly onto modern agentic LLM workflows:

| Intelligence stage | LLM agentic analog | Key LLM-side failure mode |
|---|---|---|
| Direction | System prompt / user request | [[concepts/anchoring-bias\|Anchoring]] from prompt framing; over-narrow scoping |
| Collection | Retrieval / tool use / context assembly | Position bias in long context ([[sources/liu-lost-in-middle-2023\|Liu 2023]]); RAG retrieval gaps |
| Processing | Filtering, deduplication, chunking | Chunk-boundary context loss ([[sources/roberts-llm-sats-ftw-2025\|Roberts 2025]]); over-aggressive filtering |
| Analysis | Reasoning step / chain-of-thought / agent decisions | [[concepts/sycophancy\|Sycophancy]], [[concepts/hallucination\|hallucination]], [[concepts/premature-closure\|premature closure]], [[concepts/confirmation-bias\|confirmation bias]] |
| Dissemination | Output formatting / synthesis / handoff | [[concepts/overconfidence-bias\|Overconfidence]] in stated conclusions; loss of caveats; [[concepts/persona-capture\|persona]] artifacts in delivery |

**The mapping isn't metaphorical — it is structural.** Both pipelines:
- Take an unstructured question and produce an analytic product
- Compound errors across stages
- Have most-attention paid to the analysis stage, but most-cause-of-failure distributed across all stages
- Benefit from structural interventions ([[concepts/structured-analytic-techniques|SATs]]) rather than asking individual stages to "try harder"

---

## Why This Matters for the SAT-LLM Thesis

A single SAT intervention at the analysis stage cannot fix a flawed cycle. The wiki's [[synthesis/sat-pipeline|SAT Pipeline]] page describes how to compose SATs across stages; this concept page provides the underlying framework for *why* multi-stage composition is the right unit of work.

It also informs [[synthesis/bias-evals|Bias Evaluations]]: judges need to be applied per-stage, not only to the final output, because failures at earlier stages produce traces that look reasonable at the analysis stage but were doomed at collection.

---

## Sources

- [[sources/grey-dynamics-intelligence-failure-2024|Grey Dynamics — Intelligence Failure (2024)]] — concise practitioner overview of the cycle with case studies (Iraq 2003, Russia/Ukraine 2022) at each stage
- [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] — embeds the cycle implicitly throughout; SATs are positioned as interventions primarily at the analysis stage

## See Also

- [[synthesis/sat-pipeline|SAT Pipeline]] — how to apply SATs across the stages
- [[synthesis/bias-evals|Bias Evaluations]] — per-stage measurement
- [[concepts/cognitive-bias|Cognitive Bias]] — the analysis-stage failure mode the wiki focuses on
- [[concepts/structured-analytic-techniques|Structured Analytic Techniques]] — the toolkit applied at the analysis stage
