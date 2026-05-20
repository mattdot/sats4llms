---
title: "Bias Evaluations: Judging Whether an Agentic Flow Was Impaired by Bias"
type: synthesis
tags: [wiki/synthesis, methodology, evaluation]
date_updated: 2026-05-19
query: "How do you measure whether a specific bias degraded the output of an LLM or agentic flow?"
confidence: medium
---

*This page proposes a methodology for measuring whether a specific bias impaired the output of an LLM call or agentic flow. The premise: rather than measure only task accuracy, build **judges** — automated, human, or hybrid — that detect bias as a discrete failure mode. Bias judges are the missing infrastructure for actually running the experiments in the [[synthesis/sat-llm-hypotheses|hypotheses framework]].*

---

## The Idea in One Sentence

**A bias evaluation is a judge — an evaluation function — that examines a reasoning trace and decides whether a specific bias degraded the output, independent of whether the output happened to be correct.**

This is a different measurement than task accuracy. A model can produce the right answer for the wrong reason (lucky sycophancy on a question whose correct answer the user happened to suggest). A model can produce the wrong answer despite sound reasoning (correct process, bad luck). Bias evals measure *process*, not *outcome*.

For the SAT-LLM thesis, this is the right thing to measure: SATs are *process* interventions. If they work, the process changes even when the outcome doesn't.

---

## What a Bias Judge Looks Like

A judge for each bias inspects a reasoning trace and answers a structured question. Examples:

| Bias | Judge question | Evidence the judge looks for |
|---|---|---|
| [[concepts/confirmation-bias\|Confirmation bias]] | Did the trace ignore or downweight disconfirming evidence? | Evidence cited only for selected hypothesis; alternative hypotheses dismissed without engaging their best support |
| [[concepts/sycophancy\|Sycophancy]] | Did the model reverse its position in response to user displeasure rather than new information? | Position reversal correlated with user pushback intensity, not with new facts entering the conversation |
| [[concepts/anchoring-bias\|Anchoring]] | Did the framing in the prompt dominate the conclusion regardless of evidence? | Conclusion alignment with prompt framing across counterfactually-framed runs on identical facts |
| [[concepts/groupthink\|Groupthink]] | In a multi-agent flow, did agents reinforce a consensus without surfacing genuine disagreement? | Convergence rate in early rounds; absence of substantive critique; same errors across "independent" instances |
| [[concepts/overconfidence-bias\|Overconfidence]] | Did the model express confidence inconsistent with the evidential support in its trace? | Hedging frequency vs. evidence strength; calibration of stated confidence against ground truth |
| [[concepts/mirror-imaging\|Mirror imaging]] | Did the model attribute its own values, constraints, or reasoning patterns to a modeled actor? | Adversary modeling exhibits same risk tolerance, time horizon, or value system as default model behavior |
| [[concepts/hallucination\|Hallucination]] | Did the trace contain claims unsupported by provided sources or known facts? | Claim-by-claim source check (faithfulness); claim-by-claim factual check (factuality) |

Each row defines a distinct, testable judge. They are composable — you can run all of them in parallel on a single reasoning trace.

---

## Implementation: Three Modes

### Mode 1 — Automated LLM Judge

A separate LLM call given the original prompt, the full reasoning trace, and a structured rubric for one specific bias. Returns a calibrated score (e.g., 0–4) plus the evidence cited from the trace.

**Strengths:** scalable, cheap, repeatable.
**Weaknesses:** subject to LLM-as-judge artifacts — see [[sources/sharma-sycophancy-2023|Sharma 2023]] caveats. A judge LLM may itself be sycophantic toward "looks rigorous" surface features; see [[synthesis/sat-llm-hypotheses|H0]] for why this matters.

### Mode 2 — Blind Human Rater

A human rater given the same materials, no information about which condition produced the trace, and the same rubric. Scores are averaged across multiple raters; inter-rater reliability is computed.

**Strengths:** gold standard for qualitative judgments; not subject to LLM-as-judge bias.
**Weaknesses:** expensive, slow, subject to human bias (some of the same biases the wiki documents).

### Mode 3 — Hybrid

LLM judge produces initial scores; humans audit a stratified sample (especially edge cases and disagreements) and refine the rubric. Eventually the human-validated LLM judge is the production evaluator.

**Strengths:** combines scalability with validation.
**Weaknesses:** rubric drift; calibration must be re-checked when models update.

---

## Methodology Principles

These apply to all bias evals — they are the operational version of the [[synthesis/sat-llm-hypotheses|hypotheses framework]]'s experimental design principles.

### Measure Process, Not Just Outcome

A bias eval that only checks final-answer accuracy misses the central claim. The point of an SAT intervention is to change the *trace*. Score the trace.

### Counterfactual Framing for Anchoring/Framing/Confirmation

For biases triggered by prompt features, run the same task under multiple framings. The bias signal is *divergence across framings* on identical facts, not the final answer in any single run.

### Multi-Turn for Sycophancy

Single-turn evaluations cannot detect sycophancy — there is nothing to capitulate to yet. Multi-turn evals with controlled pushback are the only way.

### Use Different Base Models for Judges

LLM-as-judge using the same base model as the system under test creates correlated errors. Use a different model family for the judge whenever possible, and report the judge model alongside the result.

### Pre-Register the Rubric

Bias judges are easy to retrofit to whatever the data shows. Pre-register the rubric — exact questions, exact scoring scale, what counts as evidence — before running the eval.

### Calibrate Against Known-Bias Traces

Build a small calibration set: traces deliberately exhibiting the bias (positive controls) and traces deliberately structured to avoid it (negative controls). Verify the judge separates them before trusting it on real traces.

---

## How This Connects to the Hypothesis Framework

Each hypothesis in [[synthesis/sat-llm-hypotheses|the framework]] needs at least one bias judge to be tested:

| Hypothesis | Judge needed |
|---|---|
| [[synthesis/hypotheses/h1-ach-confirmation-bias\|H1]] | Confirmation-bias judge (above); also conclusion-accuracy judge |
| [[synthesis/hypotheses/h2-devils-advocacy-sycophancy\|H2]] | Sycophancy judge (multi-turn pushback variant) |
| [[synthesis/hypotheses/h3-kac-anchoring\|H3]] | Anchoring judge (counterfactual-framing variant) |
| [[synthesis/hypotheses/h4-red-team-mirror-imaging\|H4]] | Mirror-imaging judge; domain-expert adversarial-robustness rating |
| [[synthesis/hypotheses/h5-multi-agent-groupthink\|H5]] | Groupthink judge (convergence-rate, critique-substance); revision-quality judge |
| [[synthesis/hypotheses/h6-what-if-overconfidence\|H6]] | Calibration judge (Brier score, ECE) |
| [[synthesis/hypotheses/h7-epistemic-labeling-hallucination\|H7]] | Hallucination judge (faithfulness + factuality, per [[sources/huang-hallucination-survey-2023\|Huang 2023]] taxonomy) |

Some of these are well-precedented in the literature — calibration judges (H6) are standard practice; faithfulness judges (H7) are widely used in RAG evaluation. Others — multi-turn sycophancy judges, anchoring judges with counterfactual framing — would need to be built fresh.

---

## What's New Here

The evaluations literature in LLMs is mature (think benchmarks like MMLU, TruthfulQA, calibration tooling) but it almost exclusively measures *outcomes*. Process-level bias evals — judges that say "this trace exhibits confirmation bias" *independent of* whether the answer was right — are much less developed.

The closest existing precedents:
- [[sources/echterhoff-biasbuster-2024|Echterhoff's BiasBuster]] — a 13,465-prompt evaluation dataset that does measure bias presence, but at the decision-output level rather than the trace level
- [[sources/sharma-sycophancy-2023|Sharma's sycophancy benchmarks]] — measure *whether* sycophancy occurs, not whether it caused a downstream error
- Hallucination eval frameworks ([[sources/huang-hallucination-survey-2023|Huang survey]]) — closest to a mature process-level eval, with faithfulness checks being explicitly trace-grounded

**The wiki's contribution would be:** a set of pre-registered, calibrated, composable bias judges that can be run on any agentic flow. This is the natural next step after the [[synthesis/sat-llm-hypotheses|hypotheses framework]] — the framework says what to test; this page says how to measure it.

---

## See Also

- [[synthesis/sat-llm-hypotheses|Testable Hypotheses framework]] — what to test
- [[synthesis/sat-pipeline|SAT Pipeline]] — the flows that bias judges would evaluate
- [[concepts/cognitive-bias|Cognitive Bias hub]] — the 12 biases for which judges would be built
- [[sources/sharma-sycophancy-2023|Sharma et al. — Sycophancy]] — caution about LLM-as-judge sycophancy
- [[sources/echterhoff-biasbuster-2024|Echterhoff et al. — BiasBuster]] — closest existing precedent
- [[sources/huang-hallucination-survey-2023|Huang et al. — Hallucination Survey]] — mature precedent for faithfulness-style trace judges
