---
type: synthesis
tags: [wiki/synthesis]
date_updated: 2026-05-19
query: "Which SAT controls which cognitive bias? Full cross-reference matrix."
sources_used: ["[[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]", "[[Wiki/sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]]"]
confidence: high
---

# Bias × SAT Matrix

**Query:** Which [[Wiki/concepts/structured-analytic-techniques|SAT]] controls which [[Wiki/concepts/cognitive-bias|cognitive bias]]?

Quick-reference cross-index. For detail on any entry, follow the wikilinks to the individual bias or SAT pages.

---

## Matrix: SATs → Biases Controlled

| SAT | Primary Biases Controlled |
|-----|--------------------------|
| [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]] | [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] · [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] · [[Wiki/concepts/motivated-reasoning\|Motivated Reasoning]] · [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] · [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] |
| [[Wiki/concepts/quality-of-information-check\|Quality of Information Check]] | [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] · [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] · [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] · [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] |
| [[Wiki/concepts/indicators-or-signposts-of-change\|Indicators or Signposts of Change]] | [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] · [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] · [[Wiki/concepts/hindsight-bias\|Hindsight Bias]] · [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] |
| [[Wiki/concepts/analysis-of-competing-hypotheses\|Analysis of Competing Hypotheses (ACH)]] | [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] · [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] · [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] · [[Wiki/concepts/motivated-reasoning\|Motivated Reasoning]] · [[Wiki/concepts/groupthink\|Groupthink]] |
| [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]] | [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] · [[Wiki/concepts/groupthink\|Groupthink]] · [[Wiki/concepts/motivated-reasoning\|Motivated Reasoning]] · [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] · [[Wiki/concepts/mind-set\|Mind-Set]] |
| [[Wiki/concepts/team-a-team-b\|Team A/Team B]] | [[Wiki/concepts/groupthink\|Groupthink]] · [[Wiki/concepts/motivated-reasoning\|Motivated Reasoning]] · [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] |
| [[Wiki/concepts/high-impact-low-probability-analysis\|High-Impact/Low-Probability Analysis]] | [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] · [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] · [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] |
| [[Wiki/concepts/what-if-analysis\|What If? Analysis]] | [[Wiki/concepts/hindsight-bias\|Hindsight Bias]] · [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] · [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] · [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] |
| [[Wiki/concepts/brainstorming\|Brainstorming]] | [[Wiki/concepts/groupthink\|Groupthink]] · [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] · [[Wiki/concepts/framing-effect\|Framing Effect]] · [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] |
| [[Wiki/concepts/outside-in-thinking\|Outside-In Thinking]] | [[Wiki/concepts/mirror-imaging\|Mirror Imaging]] · [[Wiki/concepts/framing-effect\|Framing Effect]] · [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] |
| [[Wiki/concepts/red-team-analysis\|Red Team Analysis]] | [[Wiki/concepts/mirror-imaging\|Mirror Imaging]] · [[Wiki/concepts/framing-effect\|Framing Effect]] · [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] |
| [[Wiki/concepts/alternative-futures-analysis\|Alternative Futures Analysis]] | [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] · [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] · [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] · [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] · [[Wiki/concepts/hindsight-bias\|Hindsight Bias]] |

---

## Inverse Matrix: Biases → SATs That Counter Them

| Bias | SATs That Counter It | Coverage |
|------|---------------------|----------|
| [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] | ACH · Key Assumptions Check · What If? · Brainstorming · Alt Futures | Strong — 5 techniques |
| [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] | ACH · High-Impact/Low-Prob · Alt Futures · Indicators · Quality of Info · Outside-In · Red Team · Brainstorming | Strong — 8 techniques |
| [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] | ACH · Devil's Advocacy · Key Assumptions Check · Team A/B · Quality of Info · What If? | Strong — 6 techniques |
| [[Wiki/concepts/groupthink\|Groupthink]] | Devil's Advocacy · Team A/B · Brainstorming · Red Team · ACH | Strong — 5 techniques |
| [[Wiki/concepts/motivated-reasoning\|Motivated Reasoning]] | ACH · Devil's Advocacy · Key Assumptions Check · Team A/B | Moderate — 4 techniques |
| [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] | Key Assumptions Check · Quality of Info · High-Impact/Low-Prob · ACH · What If? · Alt Futures · Indicators | Strong — 7 techniques |
| [[Wiki/concepts/mirror-imaging\|Mirror Imaging]] | Red Team · Outside-In Thinking · Alt Futures · Devil's Advocacy | Moderate — 4 techniques |
| [[Wiki/concepts/framing-effect\|Framing Effect]] | Outside-In Thinking · Brainstorming · Alt Futures · Key Assumptions Check · Red Team | Moderate — 5 techniques |
| [[Wiki/concepts/hindsight-bias\|Hindsight Bias]] | What If? · Alt Futures · Indicators/Signposts · Key Assumptions Check | Moderate — 4 techniques |
| [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] | What If? · Alt Futures · Devil's Advocacy · Key Assumptions Check · High-Impact/Low-Prob · Indicators | Strong — 6 techniques |
| [[Wiki/concepts/mind-set\|Mind-Set]] | All SATs broadly; Key Assumptions Check most directly | Comprehensive |

---

## Coverage Gaps

Biases with **thinner** SAT coverage (fewer than 4 techniques):

| Bias | Coverage | Notes |
|------|----------|-------|
| [[Wiki/concepts/mirror-imaging\|Mirror Imaging]] | 4 techniques | Red Team is the primary; others are indirect. No dedicated diagnostic technique equivalent to ACH for adversary modeling. |
| [[Wiki/concepts/hindsight-bias\|Hindsight Bias]] | 4 techniques | What If? is the primary; other techniques provide partial coverage. |

---

## Most Versatile SATs (By Bias Coverage)

| Rank | SAT | Biases Addressed |
|------|-----|-----------------|
| 1 | [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]] | 5 biases (anchoring, confirmation, motivated reasoning, overconfidence, status quo) |
| 2 | [[Wiki/concepts/analysis-of-competing-hypotheses\|Analysis of Competing Hypotheses (ACH)]] | 5 biases (confirmation, anchoring, availability, motivated reasoning, groupthink) |
| 3 | [[Wiki/concepts/alternative-futures-analysis\|Alternative Futures Analysis]] | 5 biases (status quo, availability, anchoring, overconfidence, hindsight) |
| 4 | [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]] | 5 biases (confirmation, groupthink, motivated reasoning, status quo, mind-set) |
| 5 | [[Wiki/concepts/what-if-analysis\|What If? Analysis]] | 4 biases (hindsight, status quo, overconfidence, confirmation) |

**Implication for LLM agent design**: If you can only add one SAT-inspired pattern to an LLM agent, **Key Assumptions Check** and **ACH** have the broadest bias coverage. If you are building a multi-agent system and can only add one structural intervention, **Devil's Advocacy** (adversarial review gate) addresses the biases most likely to cause compounding errors across agent turns.

---

## LLM-Specific Bias Coverage

Cross-reference to [[Wiki/synthesis/sats-for-llm-agents|SATs for LLM Agents]] for implementation patterns:

| LLM Failure Mode | Analogous Bias | Best SAT Adaptation |
|-----------------|----------------|---------------------|
| Sycophancy | [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] + [[Wiki/concepts/groupthink\|Groupthink]] | Devil's Advocacy (adversarial review gate) |
| Hallucination with confidence | [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] | Key Assumptions Check (premise audit) + Quality of Info Check |
| Prompt anchoring | [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] | ACH multi-hypothesis prompting; separate generation from evaluation |
| Premature closure | [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] + [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] | ACH; What If? pre-mortem |
| Persona capture | [[Wiki/concepts/mirror-imaging\|Mirror Imaging]] | Red Team (explicit adversarial persona prompt) |
| Multi-agent echo chambers | [[Wiki/concepts/groupthink\|Groupthink]] | Team A/B architecture (different models/prompts); independent parallel analysis |
| Chain-of-thought confirmation | [[Wiki/concepts/motivated-reasoning\|Motivated Reasoning]] | ACH disconfirmation prompting; premise audit at each step |
| Context recency weighting | [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] | Indicators list (prospectively defined criteria resist recency drift) |

---

## See Also

[[Wiki/concepts/structured-analytic-techniques|Structured Analytic Techniques]] | [[Wiki/concepts/cognitive-bias|Cognitive Bias]] | [[Wiki/synthesis/sats-for-llm-agents|SATs for LLM Agents]]
