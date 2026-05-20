---
title: "Testable Hypotheses: SATs + LLM Quality (Framework)"
type: synthesis
tags: [wiki/synthesis]
date_updated: 2026-05-19
query: "What testable hypotheses could verify that SATs actually improve qualitative LLM output in bias-prone scenarios?"
confidence: medium
---

*This page is the **framework** for eight testable hypotheses about SATs + LLM quality. The meta-hypothesis H0 lives here (it applies to all the others). Each of H1–H7 has its own page with claim, experimental setup, failure modes, and empirical evidence — linked from the table below.*

---

## The Meta-Hypothesis (Test This First)

> **H0 — Structural compliance ≠ debiasing**

The most important hypothesis to *falsify* before everything else. Do LLMs genuinely reason differently when following SAT structure, or do they reformat the same biased output into a more rigorous-looking shell?

**Test:** Compare the semantic distance between hypotheses/conclusions in SAT-structured vs. unstructured outputs on identical inputs. Low semantic distance = compliance theater — the model is satisfying the format without changing the reasoning.

**If H0 holds (compliance without change), all downstream hypotheses are confounded.** A positive result on H1–H7 that fails H0 just means SAT-formatted outputs *look* better to raters, not that reasoning improved.

H0 is most likely confounded with [[concepts/sycophancy|sycophancy]]: models may perform SAT compliance for the same reason they sycophantically agree — the structured output signals approval to the RLHF-trained reward model. See [[sources/sharma-sycophancy-2023|Sharma 2023]] for the evidence that the reward landscape favors form over substance.

---

## The Seven Testable Hypotheses

| # | Hypothesis | Bias targeted | Empirical status |
|---|---|---|---|
| [[synthesis/hypotheses/h1-ach-confirmation-bias\|H1]] | [[concepts/analysis-of-competing-hypotheses\|ACH]] improves conclusion accuracy on ambiguous evidence | [[concepts/confirmation-bias\|Confirmation bias]] | Partial caution (Mitre 2004); untested in LLMs |
| [[synthesis/hypotheses/h2-devils-advocacy-sycophancy\|H2]] | [[concepts/devils-advocacy\|Devil's Advocacy]] maintains positions under pushback | [[concepts/sycophancy\|Sycophancy]] | Strong caution ([[sources/sharma-sycophancy-2023\|Sharma]], Nemeth 2001) |
| [[synthesis/hypotheses/h3-kac-anchoring\|H3]] | [[concepts/key-assumptions-check\|KAC]] breaks framing-driven anchoring | [[concepts/anchoring-bias\|Anchoring]] | Partial support ([[sources/echterhoff-biasbuster-2024\|Echterhoff]]) |
| [[synthesis/hypotheses/h4-red-team-mirror-imaging\|H4]] | [[concepts/red-team-analysis\|Red Team]] produces adversarially robust plans | [[concepts/mirror-imaging\|Mirror imaging]] | Caution from cultural-bias work ([[sources/durmus-global-opinions-2023\|Durmus]]) |
| [[synthesis/hypotheses/h5-multi-agent-groupthink\|H5]] | Multi-agent pipelines outperform single-agent chains | [[concepts/groupthink\|Groupthink]] | Partial support ([[sources/du-debate-2023\|Du]]); shared-model caveat |
| [[synthesis/hypotheses/h6-what-if-overconfidence\|H6]] | [[concepts/what-if-analysis\|What If?]] reduces overconfidence / improves calibration | [[concepts/overconfidence-bias\|Overconfidence]] | **Strong** ([[sources/tian-calibration-2023\|Tian]], [[sources/kadavath-know-2022\|Kadavath]]) |
| [[synthesis/hypotheses/h7-epistemic-labeling-hallucination\|H7]] | Epistemic labeling reduces confident hallucination rate | [[concepts/hallucination\|Hallucination]] | Mechanism confirmed ([[sources/kadavath-know-2022\|Kadavath]]); protocol untested |

**Bottom line:** the structural argument has empirical backing (the biases are real in LLMs, and the *mechanisms* the SATs target are internally accessible). The intervention argument — that the specific SAT protocols actually exploit those mechanisms — is largely untested. The closest existing work is [[sources/echterhoff-biasbuster-2024|Echterhoff's BiasBuster]] (partial validation of H3) and [[sources/du-debate-2023|Du's multi-agent debate]] (partial validation of H5).

H6 has the strongest mechanistic backing — Tian directly shows uncertainty prompts work, Kadavath shows the information is internally present. The specific What If? variant is the only untested piece.

---

## Experimental Design Principles

These apply to all seven hypotheses.

### Ground Truth Is the Hardest Problem

The cleanest experiments use scenarios with **known outcomes**:
- Historical incidents where the correct attribution is established
- Red team exercises with pre-tested solutions
- Factual Q&A against source documents with verifiable answers

Open-ended planning is hard to score — human rater disagreement is high, and "quality" is under-defined.

### Blind Human Rating vs. LLM-as-Judge

**LLM-as-judge introduces sycophancy toward SAT-structured outputs** — structured outputs look more rigorous and will score higher on perceived quality even if the underlying reasoning is identical. Use blind human raters for qualitative claims.

### Operationalize "Quality" Specifically

Different hypotheses target different quality dimensions:

| Hypothesis | Quality Dimension |
|------------|------------------|
| [[synthesis/hypotheses/h1-ach-confirmation-bias\|H1]] (ACH) | Conclusion accuracy against ground truth |
| [[synthesis/hypotheses/h2-devils-advocacy-sycophancy\|H2]] (Devil's Advocacy) | Resistance to social pressure / position stability |
| [[synthesis/hypotheses/h3-kac-anchoring\|H3]] (KAC) | Independence from initial framing |
| [[synthesis/hypotheses/h4-red-team-mirror-imaging\|H4]] (Red Team) | Adversarial robustness |
| [[synthesis/hypotheses/h5-multi-agent-groupthink\|H5]] (Multi-agent) | Rate of genuine self-revision |
| [[synthesis/hypotheses/h6-what-if-overconfidence\|H6]] (What If?) | Calibration of expressed confidence |
| [[synthesis/hypotheses/h7-epistemic-labeling-hallucination\|H7]] (Epistemic labeling) | Hallucination rate on verifiable claims |

These are distinct. A system that scores well on H7 (hallucination) may score poorly on H2 (sycophancy resistance) — they target different failure modes.

### The Roberts Anti-Pattern Warning

[[entities/scott-roberts|Scott Roberts]] (2025) found that single-prompt ACH is an anti-pattern — the model generates a complete narrative and then forces evidence to fit. This suggests: **format compliance is not sufficient; process order matters**. Hypotheses H1, H3, and H7 all have strict step-ordering requirements that must be enforced architecturally, not just via prompt instruction.

---

## See Also

- [[synthesis/sats-for-llm-agents|SATs for LLM Agents]] — the underlying case for why SATs should work
- [[synthesis/sat-selection-guide|SAT Selection Guide]] — which SAT to use for which bias
- [[synthesis/sat-pipeline|SAT Pipeline]] — how to chain SATs into testable workflows
- [[synthesis/bias-sat-matrix|Bias × SAT Matrix]] — full cross-reference of bias → SAT
- [[concepts/system-1-system-2|System 1 / System 2]] — theoretical explanation for why H0 may hold
