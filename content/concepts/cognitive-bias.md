---
type: concept
tags: [wiki/concept, wiki/bias]
date_updated: 2026-05-19
confidence: high
source_count: 2
---

# Cognitive Bias

Systematic errors in human perception, reasoning, and judgment caused by mental shortcuts (heuristics) and unconscious assumptions. The primary human-factors problem that [[concepts/structured-analytic-techniques|Structured Analytic Techniques]] are designed to counter.

**Theoretical root:** [[concepts/system-1-system-2|System 1 / System 2]] — [[entities/daniel-kahneman|Daniel Kahneman]] and [[entities/amos-tversky|Amos Tversky]]'s dual-process framework explains *why* biases arise (System 1 heuristics substituting for System 2 reasoning) and *why* structured techniques counter them (by forcing System 2 engagement).

**LLM-native failure modes** are also tracked here: [[concepts/sycophancy|Sycophancy]] and [[concepts/hallucination|Hallucination]] — these don't map to single human biases but are the LLM equivalents that SAT-structured prompting most directly counters.

This page is a **hub** — individual bias pages with full references are listed below.

---

## Bias Library

### Foundational (Kahneman/Tversky Heuristics-and-Biases Program)
| Bias | Short Description | Primary SAT Counter |
|------|------------------|---------------------|
| [[concepts/anchoring-bias\|Anchoring Bias]] | Over-reliance on first information; insufficient adjustment | ACH, Key Assumptions Check |
| [[concepts/availability-heuristic\|Availability Heuristic]] | Probability judged by ease of recall; vivid/recent events overweighted | ACH, High-Impact/Low-Prob, Alt Futures |
| [[concepts/overconfidence-bias\|Overconfidence Bias]] | Confidence intervals too narrow; certainty exceeds warrant | Key Assumptions Check, Quality of Info, High-Impact/Low-Prob |
| [[concepts/framing-effect\|Framing Effect]] | Logically equivalent presentations produce different judgments | Outside-In Thinking, Alt Futures, Brainstorming |
| [[concepts/status-quo-bias\|Status Quo Bias]] | Preference for current state; departures perceived as losses | What If?, Alt Futures, Devil's Advocacy |

### Social and Motivational
| Bias | Short Description | Primary SAT Counter |
|------|------------------|---------------------|
| [[concepts/confirmation-bias\|Confirmation Bias]] | Seek/weight confirming evidence; discount disconfirming | ACH (disconfirmation focus), Devil's Advocacy |
| [[concepts/groupthink\|Groupthink]] | Group cohesion overrides realistic appraisal | Devil's Advocacy, Team A/Team B, Brainstorming |
| [[concepts/motivated-reasoning\|Motivated Reasoning]] | Reasoning works backward from desired conclusion | ACH, Devil's Advocacy, Key Assumptions Check |

### Analytical/Perceptual
| Bias | Short Description | Primary SAT Counter |
|------|------------------|---------------------|
| [[concepts/mirror-imaging\|Mirror Imaging]] | Project own decision logic onto adversaries | Red Team Analysis, Outside-In Thinking |
| [[concepts/hindsight-bias\|Hindsight Bias]] | Outcomes perceived as predictable in retrospect | What If? (pre-mortem), Indicators/Signposts |
| [[concepts/mind-set\|Mind-Set]] | Fixed mental model filters/distorts incoming information | All SATs; Key Assumptions Check most directly |

### LLM-Native Failure Modes
| Bias | Short Description | Primary SAT Counter |
|------|------------------|---------------------|
| [[concepts/sycophancy\|Sycophancy]] | Agreement with user preference overrides accuracy; RLHF artifact | Devil's Advocacy, Team A/Team B, ACH |
| [[concepts/hallucination\|Hallucination]] | Confident fluent output with no factual grounding; no internal uncertainty signal | Quality of Info Check, Key Assumptions Check |

---

## Original Tradecraft Primer Taxonomy

[[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] organizes biases into four categories:

**Perceptual Biases:**
- *Expectations* → [[concepts/mind-set|Mind-Set]]
- *Resistance* → [[concepts/status-quo-bias|Status Quo Bias]]
- *Ambiguities* → related to [[concepts/framing-effect|Framing Effect]]

**Biases in Evaluating Evidence:**
- *Consistency* → [[concepts/confirmation-bias|Confirmation Bias]]
- *Missing Information* → [[concepts/overconfidence-bias|Overconfidence Bias]] (doesn't know what it doesn't know)
- *Discredited Evidence* persistence → [[concepts/status-quo-bias|Status Quo Bias]], [[concepts/motivated-reasoning|Motivated Reasoning]]

**Biases in Estimating Probabilities:**
- *Availability* → [[concepts/availability-heuristic|Availability Heuristic]]
- *Anchoring* → [[concepts/anchoring-bias|Anchoring Bias]]
- *Overconfidence* → [[concepts/overconfidence-bias|Overconfidence Bias]]

**Biases in Perceiving Causality:**
- *Rationality* → [[concepts/mirror-imaging|Mirror Imaging]]
- *Attribution* → [[concepts/mirror-imaging|Mirror Imaging]]

---

## Sources

- [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]
- [[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]]
- [[sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]] (LLM-native failure modes)
