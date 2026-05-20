---
title: "H1 — ACH Reduces Confirmation Bias in Evidence Evaluation"
type: synthesis
tags: [wiki/synthesis, hypothesis]
date_updated: 2026-05-19
parent: "[[synthesis/sat-llm-hypotheses|Testable Hypotheses (framework)]]"
targets_bias: "[[concepts/confirmation-bias|Confirmation Bias]]"
targets_sat: "[[concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses]]"
status: untested-in-llms; partial-caution-from-human-studies
---

## Claim

The multi-step [[concepts/analysis-of-competing-hypotheses|ACH]] protocol produces conclusions that better match ground truth than single-prompt "what's most likely?" queries on identical evidence.

## Why Confirmation Bias Is the Target

Without structure, LLMs anchor on the most salient hypothesis in the prompt and interpret subsequent evidence in its favor — a direct analog of [[concepts/confirmation-bias|Confirmation Bias]]. ACH is designed to break this by forcing the model to evaluate evidence *against every hypothesis* before ranking, rather than evaluating *in support of* a leading candidate.

## Experimental Setup

- Use cases with **known outcomes**: security incident post-mortems, historical intelligence failures, engineering post-mortems
- **Condition A:** free-form "what is the most likely explanation?"
- **Condition B:** ACH protocol — (1) generate all plausible hypotheses, (2) score each piece of evidence against each hypothesis independently in separate calls, (3) rank by diagnosticity
- Blind human raters score conclusion accuracy and quality of evidence handling

## What to Measure

Does ACH produce more accurate conclusions? Does it catch the correct explanation more often when it's *not* the most salient/obvious one — i.e., when the conventional-wisdom answer is wrong?

## Why It Could Fail

LLMs may generate multiple hypotheses in step 1 then collapse back to the most probable-looking one in scoring. Structural compliance without genuine multi-hypothesis tracking. See [[synthesis/sat-llm-hypotheses|H0]] — this is the concrete failure mode H0 warns about, specifically for ACH.

## Empirical Evidence

**Partial caution from human studies (no LLM ACH-vs-baseline study yet exists).**

| Source | Finding | Implication |
|---|---|---|
| [[sources/rand-rr1408-2016\|RAND RR1408 (2016)]] citing Cheikes et al. (Mitre, 2004) | Human ACH **reduced confirmation bias only among non-professional analysts**; expert analysts already exhibited what ACH formalizes | Variant test: does ACH help a general-purpose LLM more than a domain-tuned one? |
| [[sources/echterhoff-biasbuster-2024\|Echterhoff et al. (BiasBuster, 2024)]] | Confirmation bias is directly measurable in LLM decision-making across commercial and open-source models | Confirms the bias H1 targets is real and present |
| [[sources/roberts-llm-sats-ftw-2025\|Roberts (2025)]] | **Single-prompt ACH is an anti-pattern** — the model generates a narrative first and forces evidence to fit. Multi-step sequential ACH works. | Step-ordering must be architecturally enforced, not just prompt-described |

**The Mitre 2004 caveat is the most important finding.** It implies that a positive H1 result might depend on which model is used — a generalist model might benefit more than a finetuned domain expert, mirroring the human pattern.

## See Also

- [[concepts/analysis-of-competing-hypotheses|ACH]] · [[concepts/confirmation-bias|Confirmation Bias]]
- [[synthesis/sat-llm-hypotheses|Testable Hypotheses framework]]
- Sibling: [[synthesis/hypotheses/h3-kac-anchoring|H3 (KAC + Anchoring)]] — closely related, since both attack the salient-prompt-feature problem
