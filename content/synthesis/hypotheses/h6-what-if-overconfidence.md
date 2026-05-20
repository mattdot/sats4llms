---
title: "H6 — What If? Prompting Reduces Overconfidence"
type: synthesis
tags: [wiki/synthesis, hypothesis]
date_updated: 2026-05-19
parent: "[[synthesis/sat-llm-hypotheses|Testable Hypotheses (framework)]]"
targets_bias: "[[concepts/overconfidence-bias|Overconfidence Bias]]"
targets_sat: "[[concepts/what-if-analysis|What If? Analysis]]"
status: strong-mechanistic-support; specific-prompt-variant-untested
---

## Claim

Forcing an LLM to generate concrete failure scenarios via [[concepts/what-if-analysis|What If? Analysis]] before committing to a recommendation produces better-calibrated confidence expressions and more acknowledged uncertainty.

## Why Overconfidence Is the Target

[[concepts/overconfidence-bias|Overconfidence Bias]] in LLMs manifests as confident assertive language regardless of actual evidential support. What If? creates counter-scenarios that, if integrated into the final answer, should force hedging. The mechanism is well-supported: the information needed for calibration exists internally (Kadavath); structured prompts extract it (Tian).

## Experimental Setup

- Ask for a recommendation on tasks with verifiable outcomes (forecasting, planning under uncertainty, technical recommendations with measurable downstream success)
- **Condition A:** direct recommendation
- **Condition B:** What If? step first ("generate 5 specific scenarios in which this recommendation fails badly"), *then* recommendation in the same call
- **Condition C:** What If? in a *separate* call; final recommendation must explicitly cite which failure scenarios it accounts for
- Measure verbalized confidence, hedging frequency, calibration against ground-truth outcomes

## What to Measure

- Frequency of hedging language ("may", "could", "depending on") — surface signal
- Human ratings of epistemic honesty
- **Calibration of expressed certainty against ground-truth outcomes** — the rigorous measure (Brier score, expected calibration error)
- Whether failure scenarios surface in the recommendation or get ignored

## Why It Could Fail

Models may generate failure scenarios and then ignore them in the recommendation — the two generation steps may not cross-pollinate because they're far apart in the context window. Condition C (separate-call What If?) tests this by forcing explicit citation.

## Empirical Evidence

**Strongest empirical support of any hypothesis in this framework.**

| Source | Finding | Implication |
|---|---|---|
| [[sources/tian-calibration-2023\|Tian et al. (EMNLP 2023)]] | Verbalized confidence prompts recover calibration in RLHF-trained models — **~50% relative reduction** in expected calibration error on TriviaQA, SciQ, TruthfulQA | Direct evidence the mechanism works. What If? is a specific structured prompt that should activate the same effect. |
| [[sources/kadavath-know-2022\|Kadavath et al. (Anthropic, 2022)]] | Large models can produce well-calibrated assessments of their own correctness (P(True)). Self-knowledge improves with scale. | The information needed for accurate hedging exists internally — H6 is recoverable, not impossible |
| Lin, Hilton & Evans (2022) *Teaching Models to Express Uncertainty in Words* | Models can be trained or prompted to express verbalized uncertainty | Provides additional methodological precedent |

**Bottom line:** H6 has the strongest mechanistic backing of any hypothesis here. Tian shows uncertainty prompts work in general; Kadavath shows the information is there. **The open question is specifically whether What If? is the *most effective* variant** — i.e., does generating concrete failure scenarios produce better calibration than direct "how confident are you?" probes?

## See Also

- [[concepts/what-if-analysis|What If? Analysis]] · [[concepts/overconfidence-bias|Overconfidence Bias]]
- [[synthesis/sat-llm-hypotheses|Testable Hypotheses framework]]
- Sibling: [[synthesis/hypotheses/h7-epistemic-labeling-hallucination|H7 (Epistemic Labeling + Hallucination)]] — uses the same Kadavath mechanism for a different surface task
