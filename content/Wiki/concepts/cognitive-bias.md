---
type: concept
tags: [wiki/concept, wiki/bias]
date_updated: 2026-05-19
confidence: high
source_count: 2
---

# Cognitive Bias

Systematic errors in human perception, reasoning, and judgment caused by mental shortcuts (heuristics) and unconscious assumptions. The primary human-factors problem that [[Wiki/concepts/structured-analytic-techniques|Structured Analytic Techniques]] are designed to counter.

**Theoretical root:** [[Wiki/concepts/system-1-system-2|System 1 / System 2]] — [[Wiki/entities/daniel-kahneman|Daniel Kahneman]] and [[Wiki/entities/amos-tversky|Amos Tversky]]'s dual-process framework explains *why* biases arise (System 1 heuristics substituting for System 2 reasoning) and *why* structured techniques counter them (by forcing System 2 engagement).

**LLM-native failure modes** are also tracked here: [[Wiki/concepts/sycophancy|Sycophancy]] and [[Wiki/concepts/hallucination|Hallucination]] — these don't map to single human biases but are the LLM equivalents that SAT-structured prompting most directly counters.

This page is a **hub** — individual bias pages with full references are listed below.

---

## Bias Library

### Foundational (Kahneman/Tversky Heuristics-and-Biases Program)
| Bias | Short Description | Primary SAT Counter |
|------|------------------|---------------------|
| [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] | Over-reliance on first information; insufficient adjustment | ACH, Key Assumptions Check |
| [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] | Probability judged by ease of recall; vivid/recent events overweighted | ACH, High-Impact/Low-Prob, Alt Futures |
| [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] | Confidence intervals too narrow; certainty exceeds warrant | Key Assumptions Check, Quality of Info, High-Impact/Low-Prob |
| [[Wiki/concepts/framing-effect\|Framing Effect]] | Logically equivalent presentations produce different judgments | Outside-In Thinking, Alt Futures, Brainstorming |
| [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] | Preference for current state; departures perceived as losses | What If?, Alt Futures, Devil's Advocacy |

### Social and Motivational
| Bias | Short Description | Primary SAT Counter |
|------|------------------|---------------------|
| [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] | Seek/weight confirming evidence; discount disconfirming | ACH (disconfirmation focus), Devil's Advocacy |
| [[Wiki/concepts/groupthink\|Groupthink]] | Group cohesion overrides realistic appraisal | Devil's Advocacy, Team A/Team B, Brainstorming |
| [[Wiki/concepts/motivated-reasoning\|Motivated Reasoning]] | Reasoning works backward from desired conclusion | ACH, Devil's Advocacy, Key Assumptions Check |

### Analytical/Perceptual
| Bias | Short Description | Primary SAT Counter |
|------|------------------|---------------------|
| [[Wiki/concepts/mirror-imaging\|Mirror Imaging]] | Project own decision logic onto adversaries | Red Team Analysis, Outside-In Thinking |
| [[Wiki/concepts/hindsight-bias\|Hindsight Bias]] | Outcomes perceived as predictable in retrospect | What If? (pre-mortem), Indicators/Signposts |
| [[Wiki/concepts/mind-set\|Mind-Set]] | Fixed mental model filters/distorts incoming information | All SATs; Key Assumptions Check most directly |

### LLM-Native Failure Modes
| Bias | Short Description | Primary SAT Counter |
|------|------------------|---------------------|
| [[Wiki/concepts/sycophancy\|Sycophancy]] | Agreement with user preference overrides accuracy; RLHF artifact | Devil's Advocacy, Team A/Team B, ACH |
| [[Wiki/concepts/hallucination\|Hallucination]] | Confident fluent output with no factual grounding; no internal uncertainty signal | Quality of Info Check, Key Assumptions Check |

---

## Original Tradecraft Primer Taxonomy

[[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] organizes biases into four categories:

**Perceptual Biases:**
- *Expectations* → [[Wiki/concepts/mind-set|Mind-Set]]
- *Resistance* → [[Wiki/concepts/status-quo-bias|Status Quo Bias]]
- *Ambiguities* → related to [[Wiki/concepts/framing-effect|Framing Effect]]

**Biases in Evaluating Evidence:**
- *Consistency* → [[Wiki/concepts/confirmation-bias|Confirmation Bias]]
- *Missing Information* → [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]] (doesn't know what it doesn't know)
- *Discredited Evidence* persistence → [[Wiki/concepts/status-quo-bias|Status Quo Bias]], [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]]

**Biases in Estimating Probabilities:**
- *Availability* → [[Wiki/concepts/availability-heuristic|Availability Heuristic]]
- *Anchoring* → [[Wiki/concepts/anchoring-bias|Anchoring Bias]]
- *Overconfidence* → [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]]

**Biases in Perceiving Causality:**
- *Rationality* → [[Wiki/concepts/mirror-imaging|Mirror Imaging]]
- *Attribution* → [[Wiki/concepts/mirror-imaging|Mirror Imaging]]

---

## Sources

- [[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]
- [[Wiki/sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]]
- [[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]] (LLM-native failure modes)
