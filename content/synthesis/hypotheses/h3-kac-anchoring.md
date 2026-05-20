---
title: "H3 — Key Assumptions Check Prevents Anchoring Propagation"
type: synthesis
tags: [wiki/synthesis, hypothesis]
date_updated: 2026-05-19
parent: "[[synthesis/sat-llm-hypotheses|Testable Hypotheses (framework)]]"
targets_bias: "[[concepts/anchoring-bias|Anchoring Bias]]"
targets_sat: "[[concepts/key-assumptions-check|Key Assumptions Check]]"
status: partial-empirical-support
---

## Claim

Running an explicit [[concepts/key-assumptions-check|KAC]] before analysis reduces the degree to which initial framing determines final conclusions in multi-step chains.

## Why Anchoring Is the Target

[[concepts/anchoring-bias|Anchoring Bias]] in LLMs operates at the prompt level — framing in the first few hundred tokens disproportionately shapes all downstream generation. KAC forces explicit surfacing of those assumptions before reasoning proceeds, making it harder for an unexamined frame to propagate.

## Experimental Setup

- Give identical underlying facts with two different framings:
  - "this security incident was caused by insider threat" (leading frame)
  - "a security incident occurred; the cause is unknown" (neutral frame)
- **Condition A (without KAC):** measure how often final conclusions align with the initial framing regardless of evidence
- **Condition B (with KAC):** insert an explicit "list the assumptions baked into this framing" step before analysis. Then run analysis. Does it reduce framing-driven divergence?

## What to Measure

- Semantic similarity of conclusions across the two framing conditions (high similarity = framing was successfully countered)
- Degree to which framing-injected assumptions appear unchallenged in final outputs
- Whether the assumptions surfaced by KAC are actually *used* downstream (or just listed and ignored)

## Why It Could Fail

KAC identifies assumptions but naming them may not break their grip. [[concepts/system-1-system-2|System 1-analog]] generation has already been primed; explicit metacognition may be insufficient to override it. Models may list assumptions then proceed as if they had not.

## Empirical Evidence

**Partial support — the closest existing empirical work.**

| Source | Finding | Implication |
|---|---|---|
| [[sources/echterhoff-biasbuster-2024\|Echterhoff et al. (BiasBuster, 2024)]] | Anchoring is one of the strongest measured biases in LLM decision-making. **Self-debiasing prompts** (asking the model to identify and counter its own bias) reduce the effect. | The self-debiasing prompt is functionally a KAC variant. This is the best existing partial validation of H3. |
| [[sources/echterhoff-biasbuster-2024\|Echterhoff et al. (2024)]] | The mitigation approach transfers — a single self-debiasing pattern reduces multiple bias types | A general KAC may work across multiple biases, not just anchoring |
| [[sources/roberts-llm-sats-ftw-2025\|Roberts (2025)]] | **Cross-chunk context loss** breaks KAC on long documents — assumptions surfaced in early chunks are lost by the time later chunks are processed | H3 likely holds for single-context analysis but degrades for long-document agentic pipelines. Sliding-window or map-reduce mitigation needed. |

**Open: does the Echterhoff self-debiasing finding hold up in multi-turn agentic chains where bias can propagate across turns?** Their study tests isolated decisions.

## See Also

- [[concepts/key-assumptions-check|Key Assumptions Check]] · [[concepts/anchoring-bias|Anchoring Bias]] · [[concepts/framing-effect|Framing Effect]]
- [[synthesis/sat-llm-hypotheses|Testable Hypotheses framework]]
- Sibling: [[synthesis/hypotheses/h1-ach-confirmation-bias|H1 (ACH + Confirmation)]] — both attack salient-feature dominance
