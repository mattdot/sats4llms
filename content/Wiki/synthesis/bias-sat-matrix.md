---
type: synthesis
tags: [wiki/synthesis]
date_updated: 2026-05-19
query: "Which SAT controls which cognitive bias? Full cross-reference matrix."
sources_used: ["[[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]", "[[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]]"]
confidence: high
---

# Bias × SAT Matrix

**Query:** Which [[concepts/structured-analytic-techniques|SAT]] controls which [[concepts/cognitive-bias|cognitive bias]]?

Quick-reference cross-index. For detail on any entry, follow the wikilinks to the individual bias or SAT pages.

---

## Matrix: SATs → Biases Controlled

| SAT | Primary Biases Controlled |
|-----|--------------------------|
| [[concepts/key-assumptions-check\|Key Assumptions Check]] | [[concepts/anchoring-bias\|Anchoring Bias]] · [[concepts/confirmation-bias\|Confirmation Bias]] · [[concepts/motivated-reasoning\|Motivated Reasoning]] · [[concepts/overconfidence-bias\|Overconfidence Bias]] · [[concepts/status-quo-bias\|Status Quo Bias]] |
| [[concepts/quality-of-information-check\|Quality of Information Check]] | [[concepts/overconfidence-bias\|Overconfidence Bias]] · [[concepts/confirmation-bias\|Confirmation Bias]] · [[concepts/availability-heuristic\|Availability Heuristic]] · [[concepts/anchoring-bias\|Anchoring Bias]] |
| [[concepts/indicators-or-signposts-of-change\|Indicators or Signposts of Change]] | [[concepts/availability-heuristic\|Availability Heuristic]] · [[concepts/status-quo-bias\|Status Quo Bias]] · [[concepts/hindsight-bias\|Hindsight Bias]] · [[concepts/overconfidence-bias\|Overconfidence Bias]] |
| [[concepts/analysis-of-competing-hypotheses\|Analysis of Competing Hypotheses (ACH)]] | [[concepts/confirmation-bias\|Confirmation Bias]] · [[concepts/anchoring-bias\|Anchoring Bias]] · [[concepts/availability-heuristic\|Availability Heuristic]] · [[concepts/motivated-reasoning\|Motivated Reasoning]] · [[concepts/groupthink\|Groupthink]] |
| [[concepts/devils-advocacy\|Devil's Advocacy]] | [[concepts/confirmation-bias\|Confirmation Bias]] · [[concepts/groupthink\|Groupthink]] · [[concepts/motivated-reasoning\|Motivated Reasoning]] · [[concepts/status-quo-bias\|Status Quo Bias]] · [[concepts/mind-set\|Mind-Set]] |
| [[concepts/team-a-team-b\|Team A/Team B]] | [[concepts/groupthink\|Groupthink]] · [[concepts/motivated-reasoning\|Motivated Reasoning]] · [[concepts/confirmation-bias\|Confirmation Bias]] |
| [[concepts/high-impact-low-probability-analysis\|High-Impact/Low-Probability Analysis]] | [[concepts/availability-heuristic\|Availability Heuristic]] · [[concepts/overconfidence-bias\|Overconfidence Bias]] · [[concepts/status-quo-bias\|Status Quo Bias]] |
| [[concepts/what-if-analysis\|What If? Analysis]] | [[concepts/hindsight-bias\|Hindsight Bias]] · [[concepts/status-quo-bias\|Status Quo Bias]] · [[concepts/overconfidence-bias\|Overconfidence Bias]] · [[concepts/confirmation-bias\|Confirmation Bias]] |
| [[concepts/brainstorming\|Brainstorming]] | [[concepts/groupthink\|Groupthink]] · [[concepts/anchoring-bias\|Anchoring Bias]] · [[concepts/framing-effect\|Framing Effect]] · [[concepts/availability-heuristic\|Availability Heuristic]] |
| [[concepts/outside-in-thinking\|Outside-In Thinking]] | [[concepts/mirror-imaging\|Mirror Imaging]] · [[concepts/framing-effect\|Framing Effect]] · [[concepts/availability-heuristic\|Availability Heuristic]] |
| [[concepts/red-team-analysis\|Red Team Analysis]] | [[concepts/mirror-imaging\|Mirror Imaging]] · [[concepts/framing-effect\|Framing Effect]] · [[concepts/availability-heuristic\|Availability Heuristic]] |
| [[concepts/alternative-futures-analysis\|Alternative Futures Analysis]] | [[concepts/status-quo-bias\|Status Quo Bias]] · [[concepts/availability-heuristic\|Availability Heuristic]] · [[concepts/anchoring-bias\|Anchoring Bias]] · [[concepts/overconfidence-bias\|Overconfidence Bias]] · [[concepts/hindsight-bias\|Hindsight Bias]] |

---

## Inverse Matrix: Biases → SATs That Counter Them

| Bias | SATs That Counter It | Coverage |
|------|---------------------|----------|
| [[concepts/anchoring-bias\|Anchoring Bias]] | ACH · Key Assumptions Check · What If? · Brainstorming · Alt Futures | Strong — 5 techniques |
| [[concepts/availability-heuristic\|Availability Heuristic]] | ACH · High-Impact/Low-Prob · Alt Futures · Indicators · Quality of Info · Outside-In · Red Team · Brainstorming | Strong — 8 techniques |
| [[concepts/confirmation-bias\|Confirmation Bias]] | ACH · Devil's Advocacy · Key Assumptions Check · Team A/B · Quality of Info · What If? | Strong — 6 techniques |
| [[concepts/groupthink\|Groupthink]] | Devil's Advocacy · Team A/B · Brainstorming · Red Team · ACH | Strong — 5 techniques |
| [[concepts/motivated-reasoning\|Motivated Reasoning]] | ACH · Devil's Advocacy · Key Assumptions Check · Team A/B | Moderate — 4 techniques |
| [[concepts/overconfidence-bias\|Overconfidence Bias]] | Key Assumptions Check · Quality of Info · High-Impact/Low-Prob · ACH · What If? · Alt Futures · Indicators | Strong — 7 techniques |
| [[concepts/mirror-imaging\|Mirror Imaging]] | Red Team · Outside-In Thinking · Alt Futures · Devil's Advocacy | Moderate — 4 techniques |
| [[concepts/framing-effect\|Framing Effect]] | Outside-In Thinking · Brainstorming · Alt Futures · Key Assumptions Check · Red Team | Moderate — 5 techniques |
| [[concepts/hindsight-bias\|Hindsight Bias]] | What If? · Alt Futures · Indicators/Signposts · Key Assumptions Check | Moderate — 4 techniques |
| [[concepts/status-quo-bias\|Status Quo Bias]] | What If? · Alt Futures · Devil's Advocacy · Key Assumptions Check · High-Impact/Low-Prob · Indicators | Strong — 6 techniques |
| [[concepts/mind-set\|Mind-Set]] | All SATs broadly; Key Assumptions Check most directly | Comprehensive |

---

## Coverage Gaps

Biases with **thinner** SAT coverage (fewer than 4 techniques):

| Bias | Coverage | Notes |
|------|----------|-------|
| [[concepts/mirror-imaging\|Mirror Imaging]] | 4 techniques | Red Team is the primary; others are indirect. No dedicated diagnostic technique equivalent to ACH for adversary modeling. |
| [[concepts/hindsight-bias\|Hindsight Bias]] | 4 techniques | What If? is the primary; other techniques provide partial coverage. |

---

## Most Versatile SATs (By Bias Coverage)

| Rank | SAT | Biases Addressed |
|------|-----|-----------------|
| 1 | [[concepts/key-assumptions-check\|Key Assumptions Check]] | 5 biases (anchoring, confirmation, motivated reasoning, overconfidence, status quo) |
| 2 | [[concepts/analysis-of-competing-hypotheses\|Analysis of Competing Hypotheses (ACH)]] | 5 biases (confirmation, anchoring, availability, motivated reasoning, groupthink) |
| 3 | [[concepts/alternative-futures-analysis\|Alternative Futures Analysis]] | 5 biases (status quo, availability, anchoring, overconfidence, hindsight) |
| 4 | [[concepts/devils-advocacy\|Devil's Advocacy]] | 5 biases (confirmation, groupthink, motivated reasoning, status quo, mind-set) |
| 5 | [[concepts/what-if-analysis\|What If? Analysis]] | 4 biases (hindsight, status quo, overconfidence, confirmation) |

**Implication for LLM agent design**: If you can only add one SAT-inspired pattern to an LLM agent, **Key Assumptions Check** and **ACH** have the broadest bias coverage. If you are building a multi-agent system and can only add one structural intervention, **Devil's Advocacy** (adversarial review gate) addresses the biases most likely to cause compounding errors across agent turns.

---

## LLM-Specific Bias Coverage

Cross-reference to [[synthesis/sats-for-llm-agents|SATs for LLM Agents]] for implementation patterns:

| LLM Failure Mode | Analogous Bias | Best SAT Adaptation |
|-----------------|----------------|---------------------|
| Sycophancy | [[concepts/confirmation-bias\|Confirmation Bias]] + [[concepts/groupthink\|Groupthink]] | Devil's Advocacy (adversarial review gate) |
| Hallucination with confidence | [[concepts/overconfidence-bias\|Overconfidence Bias]] | Key Assumptions Check (premise audit) + Quality of Info Check |
| Prompt anchoring | [[concepts/anchoring-bias\|Anchoring Bias]] | ACH multi-hypothesis prompting; separate generation from evaluation |
| Premature closure | [[concepts/anchoring-bias\|Anchoring Bias]] + [[concepts/status-quo-bias\|Status Quo Bias]] | ACH; What If? pre-mortem |
| Persona capture | [[concepts/mirror-imaging\|Mirror Imaging]] | Red Team (explicit adversarial persona prompt) |
| Multi-agent echo chambers | [[concepts/groupthink\|Groupthink]] | Team A/B architecture (different models/prompts); independent parallel analysis |
| Chain-of-thought confirmation | [[concepts/motivated-reasoning\|Motivated Reasoning]] | ACH disconfirmation prompting; premise audit at each step |
| Context recency weighting | [[concepts/availability-heuristic\|Availability Heuristic]] | Indicators list (prospectively defined criteria resist recency drift) |

---

## See Also

[[concepts/structured-analytic-techniques|Structured Analytic Techniques]] | [[concepts/cognitive-bias|Cognitive Bias]] | [[synthesis/sats-for-llm-agents|SATs for LLM Agents]]
