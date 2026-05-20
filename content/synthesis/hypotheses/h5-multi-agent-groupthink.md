---
title: "H5 — Multi-Agent SAT Pipelines Outperform Single-Agent Chains"
type: synthesis
tags: [wiki/synthesis, hypothesis]
date_updated: 2026-05-19
parent: "[[synthesis/sat-llm-hypotheses|Testable Hypotheses (framework)]]"
targets_bias: "[[concepts/groupthink|Groupthink]]"
targets_sat: "[[concepts/team-a-team-b|Team A/Team B]] / multi-agent debate"
status: partial-empirical-support
---

## Claim

A pipeline with separate agents for (a) claim generation and (b) adversarial critique produces higher quality outputs than a single agent doing both, because multi-agent separation prevents [[concepts/status-quo-bias|self-consistency pressure]] from suppressing genuine challenge.

## Why Groupthink Is the Target

[[concepts/groupthink|Groupthink]] in LLM systems emerges when a single model's prior outputs anchor subsequent generation — the model becomes motivated to maintain consistency with itself. Separate agents with no shared context lack this self-consistency pressure. The architectural analog of the [[concepts/team-a-team-b|Team A/Team B]] technique.

## Experimental Setup

- Same analytical task run in:
  - **Condition A:** single agent chain (generate → self-critique → revise, all in one context)
  - **Condition B:** two-agent pipeline (generator + separate critic; critic has no access to generator's reasoning chain, only its final output)
  - **Condition C (control for shared base model):** condition B but using *different* base models for generator and critic
- Blind human raters score final output quality and intellectual honesty
- Measure rate of caught contradictions, revised conclusions, acknowledged uncertainty

## What to Measure

- Rate of self-revision in the pipeline
- Quality of caught errors (substantive vs. cosmetic)
- Whether conclusions actually *change* between generation and post-critique, or just get reworded
- The critical comparison: how much of B-over-A improvement is *retained* in C? (Tests whether the structure or the genuine independence is doing the work)

## Why It Could Fail

If both agents share the same base model, they may have identical biases and miss the same things — no genuine epistemic independence. The critique agent may find only surface errors while missing the shared blind spots. This is what condition C is designed to expose.

## Empirical Evidence

**Partial validation. Du 2023 confirms the structure works; the open question is whether genuine independence matters.**

| Source | Finding | Implication |
|---|---|---|
| [[sources/du-debate-2023\|Du et al. (MIT, 2023)]] | Multi-instance multi-round debate **significantly improves factuality and reasoning**, reduces hallucination, across math, reasoning, factual QA benchmarks | Direct partial validation of H5 (conditions A vs B) |
| [[sources/du-debate-2023\|Du et al. (2023)]] caveat | All "instances" in Du's experiments share the **same base model** | The critical question H5 asks — does *genuine* independence matter? — is exactly what Du does not test |
| Liang et al. (2023) *Encouraging Divergent Thinking via Multi-Agent Debate* | Multi-agent debate increases response diversity | Suggests structure-alone contributes, but again same-model |

**The C condition is the key contribution of H5.** No published study compares same-model multi-agent vs. different-model multi-agent. If different-model significantly outperforms same-model, this confirms genuine groupthink-control matters. If they're similar, the win is the structure (which is still useful but means cheaper architectures suffice).

## See Also

- [[concepts/groupthink|Groupthink]] · [[concepts/team-a-team-b|Team A/Team B]] · [[concepts/devils-advocacy|Devil's Advocacy]]
- [[synthesis/sat-pipeline|SAT Pipeline]] — Pattern B (parallel + adversarial) is the H5 architecture
- Sibling: [[synthesis/hypotheses/h2-devils-advocacy-sycophancy|H2 (Devil's Advocacy + Sycophancy)]] — H2 condition (d) is essentially a one-shot H5
