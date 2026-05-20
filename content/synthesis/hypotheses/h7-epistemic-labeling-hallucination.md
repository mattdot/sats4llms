---
title: "H7 — Epistemic Labeling Reduces Confident Hallucination"
type: synthesis
tags: [wiki/synthesis, hypothesis]
date_updated: 2026-05-19
parent: "[[synthesis/sat-llm-hypotheses|Testable Hypotheses (framework)]]"
targets_bias: "[[concepts/hallucination|Hallucination]]"
targets_sat: "epistemic-labeling (KAC variant)"
status: mechanism-confirmed; specific-protocol-untested
---

## Claim

Adding an explicit epistemic labeling step before synthesis — "classify each factual claim as: (a) directly stated in source, (b) inferred from source, (c) uncertain, (d) speculative" — reduces the rate of confident [[concepts/hallucination|hallucination]] on verifiable facts.

## Why Hallucination Is the Target

[[concepts/hallucination|Hallucination]] is driven partly by the absence of any internal uncertainty signal in the *generation pathway*. Forcing the model to classify its own claims before synthesizing them creates a structured opportunity to surface that uncertainty before it gets flattened into confident prose. Per [[sources/kadavath-know-2022|Kadavath]], the information is there; H7 is a structured query for it.

## Experimental Setup

- Feed source documents + questions with verifiable answers against those documents (faithfulness task) and against the world (factuality task — see [[sources/huang-hallucination-survey-2023|Huang 2023]] for the split)
- **Condition A:** synthesize directly
- **Condition B:** label each claim first (a/b/c/d), then synthesize with labels preserved as hedges in the final output
- **Condition C:** label each claim, but force the model to *drop* claims labeled (c) or (d) before synthesis (stricter variant)

## What to Measure

- **Rate of hallucinated claims** (claims not supportable by source — faithfulness; claims false about the world — factuality)
- Rate of appropriate hedging on uncertain claims
- **Meta-accuracy**: whether "directly stated" labels are themselves accurate (does the model correctly identify what's in the source vs. what it made up?)

## Why It Could Fail

Models may label their hallucinations as "directly stated" — the labeling step is itself subject to hallucination. Meta-accuracy (knowing what you know) is not guaranteed. The Kadavath finding gives mechanistic hope but not certainty for this specific task framing.

## Empirical Evidence

**Mechanism confirmed; specific protocol untested.**

| Source | Finding | Implication |
|---|---|---|
| [[sources/kadavath-know-2022\|Kadavath et al. (Anthropic, 2022)]] | Models can be prompted/trained to produce well-calibrated P(True) for their own outputs. **The information is internally present.** | H7's mechanism is plausible — labeling extracts information that exists |
| [[sources/huang-hallucination-survey-2023\|Huang et al. (2023)]] | Canonical taxonomic split: *faithfulness* (claim unsupported by source) vs. *factuality* (claim wrong about world). RAG does not eliminate either. | H7 is most plausible for faithfulness (the model can check against provided source); factuality is harder because no ground reference |
| [[sources/tian-calibration-2023\|Tian et al. (2023)]] | Verbalized uncertainty prompts work — the simple intervention is "just ask" | Strong precedent that structured queries for uncertainty extract usable signal |

**Practical implication:** H7 likely succeeds on *faithfulness* (especially in condition C, where uncertain claims are dropped). Factuality improvements are less likely without external grounding. Two distinct tests should be reported separately.

**Open: meta-accuracy of the labels themselves.** A pre-registered measurement: for each "directly stated" label, check whether the claim is verbatim or near-verbatim in the source. This is the test of whether the labeling step is doing real work.

## See Also

- [[concepts/hallucination|Hallucination]] · [[concepts/key-assumptions-check|Key Assumptions Check]]
- [[synthesis/sat-llm-hypotheses|Testable Hypotheses framework]]
- Sibling: [[synthesis/hypotheses/h6-what-if-overconfidence|H6 (What If? + Overconfidence)]] — same Kadavath mechanism, different surface task
- [[sources/huang-hallucination-survey-2023|Huang Hallucination Survey]] — for the faithfulness/factuality distinction
