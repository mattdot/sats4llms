---
title: SATs for LLMs
type: overview
tags: [wiki/overview]
aliases: [overview]
date_updated: 2026-05-19
source_count: 3
---

# SATs for LLMs — Overview

---

## The Central Thesis

LLMs have systematic reasoning failures that are structurally analogous to the cognitive biases that have plagued human intelligence analysis for decades. The intelligence community spent fifty years developing **Structured Analytic Techniques (SATs)** — a family of methods that counter those biases not by asking analysts to *try harder*, but by changing the *structure of the reasoning process itself*.

That same structural logic applies to LLM agents. Because agents are software, the interventions can be implemented as **architectural patterns and prompt protocols** — not just advisory guidelines. This wiki explores how.

---

## Why SATs, Why Now

Three things converge to make this worth building:

**1. The bias problem is real and well-characterized.** Human cognitive biases — confirmation bias, anchoring, groupthink, overconfidence, mirror imaging — are not vague tendencies. They are documented failure modes with known mechanisms, studied extensively in intelligence analysis contexts where the cost of being wrong is high. The CIA's Tradecraft Primer (2009) documents 12 techniques specifically designed to counter them structurally.

**2. LLMs exhibit analogous failure modes.** Sycophancy mirrors confirmation bias. Prompt anchoring mirrors anchoring bias. Multi-agent echo chambers mirror groupthink. Hallucination with confidence mirrors overconfidence. Persona capture mirrors mirror imaging. The parallel is close enough that the SAT countermeasures translate directly.

**3. Implementation is now proven, not theoretical.** [[entities/scott-roberts|Scott Roberts]] (SANS 2025) built working Streamlit + GPT-4 tools implementing Starbursting, ACH, and Key Assumptions Check, ran them on real problems, and published the code. The key finding: SAT-structured LLM workflows work — but some techniques (especially ACH) require multi-step orchestration rather than single prompts, and long-document analysis hits token-limit failure modes that need architectural mitigations.

---

## The Structural Parallel

| Human Analysis Problem | LLM Equivalent | SAT Countermeasure |
|------------------------|----------------|-------------------|
| Confirmation bias | Sycophancy / prompt confirmation | [[concepts/analysis-of-competing-hypotheses\|ACH]], [[concepts/devils-advocacy\|Devil's Advocacy]] |
| Anchoring bias | Prompt framing lock-in | [[concepts/key-assumptions-check\|Key Assumptions Check]], generate-then-evaluate separation |
| Groupthink | Multi-agent echo chambers | [[concepts/team-a-team-b\|Team A/Team B]], independent parallel analysis |
| Overconfidence | Hallucination with false certainty | [[concepts/what-if-analysis\|What If? Analysis]], explicit uncertainty tracking |
| Mirror imaging | Persona capture | [[concepts/red-team-analysis\|Red Team Analysis]] |
| Premature closure | Single-hypothesis generation | [[concepts/starbursting\|Starbursting]], [[concepts/brainstorming\|Brainstorming]] |

---

## Key Themes

1. **SATs are structural, not aspirational.** They don't ask analysts (or agents) to be less biased — they change the process so the bias has nowhere to operate. This is why they translate to software.

2. **Disconfirmation over confirmation.** The most rigorous SATs ([[concepts/analysis-of-competing-hypotheses|ACH]], [[concepts/devils-advocacy|Devil's Advocacy]]) are built around *disproving* hypotheses rather than confirming them. Single-prompt LLM calls that generate and evaluate in one step defeat this structure — sequential calls are required.

3. **Human-machine team, not replacement.** Roberts' empirical finding: LLMs handle the structural work (generating hypotheses, surfacing assumptions, mapping question space) while humans handle judgment (reviewing CSV output, adjusting scores, making final calls). The value is making rigorous SAT processes tractable for small teams.

4. **The bias library matters.** Nine individual biases are documented in this wiki with academic citations, mechanisms, and specific SAT countermeasures. Knowing *which* bias a technique targets tells you *when* to apply it and *how* to structure the prompt.

---

## The Technique Inventory

**Diagnostic** *(make gaps and assumptions transparent)*
[[concepts/key-assumptions-check|Key Assumptions Check]] · [[concepts/quality-of-information-check|Quality of Information Check]] · [[concepts/indicators-or-signposts-of-change|Indicators or Signposts of Change]] · [[concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses (ACH)]]

**Contrarian** *(challenge current thinking)*
[[concepts/devils-advocacy|Devil's Advocacy]] · [[concepts/team-a-team-b|Team A/Team B]] · [[concepts/high-impact-low-probability-analysis|High-Impact/Low-Probability Analysis]] · [[concepts/what-if-analysis|What If? Analysis]]

**Imaginative** *(generate new perspectives and scope problems)*
[[concepts/brainstorming|Brainstorming]] · [[concepts/outside-in-thinking|Outside-In Thinking]] · [[concepts/red-team-analysis|Red Team Analysis]] · [[concepts/alternative-futures-analysis|Alternative Futures Analysis]] · [[concepts/starbursting|Starbursting]]

---

## Key Synthesis Pages

- [[synthesis/sats-for-llm-agents|SATs for LLM Agents]] — the core synthesis: bias taxonomy, 8 SAT prompt adaptations, architectural patterns, empirical evidence
- [[synthesis/bias-sat-matrix|Bias x SAT Matrix]] — full cross-reference: which SAT controls which bias, in both directions

---

## Open Questions

- How do SAT-structured prompts interact with chain-of-thought? Does CoT amplify or reduce the targeted biases?
- Can ACH's cross-chunk context loss in long documents be fully mitigated by map-reduce or sliding-window approaches?
- What does RAND RR1408 add? (Currently inaccessible — 403)
- The Heuer/Pherson book (*Structured Analytic Techniques for Intelligence Analysis*, 3rd ed.) covers a broader technique set than the CIA Primer — worth ingesting if accessible.

---

*See [[catalog|Catalog]] for the full catalog. Last updated after ingesting 3 sources.*
