---
type: concept
tags: [wiki/concept, wiki/bias]
date_updated: 2026-05-19
confidence: high
source_count: 1
---

# Overconfidence Bias

The systematic tendency to **overestimate the accuracy of one's own knowledge and judgments**. Manifests as probability calibration errors (confidence intervals are too narrow), excessive certainty about predictions, and underestimation of uncertainty and tail risks.

---

## Origin

Extensively documented by Kahneman & Tversky and their colleagues from the 1970s onward. The *calibration* literature (Fischhoff, Slovic, Lichtenstein) demonstrated that even experts produce confidence intervals that are far too narrow — people who say they are "90% confident" are correct far less than 90% of the time.

Classic demonstration: subjects asked to provide 90% confidence intervals for trivia questions (e.g., "How many airports are in the US?"). Actual hit rate for "90% confident" ranges: approximately 40–60% rather than 90%.

---

## Subtypes

**Overprecision** — excessive certainty about the accuracy of one's beliefs (the core form; confidence intervals too narrow)

**Overplacement** — believing oneself to be above average (the "Lake Wobegon effect" — most people believe they are above-average drivers, managers, etc.)

**Overestimation** — overestimating one's absolute performance level

---

## Intelligence Analysis Context (per [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]])

Named in the primer's probability-estimation bias taxonomy:
> "In translating feelings of certainty into a probability estimate, people are often overconfident, especially if they have considerable expertise."

Critically: expertise *increases* overconfidence in some domains, not decreases it. This is the Dunning-Kruger inversion at the expert level — experts have learned enough to be confidently wrong in systematic ways.

The 2003 Iraq WMD assessment is the canonical intelligence failure of overconfidence — assessments were stated with high confidence despite thin and ambiguous sourcing.

---

## LLM Agentic Systems Context

LLM agents exhibit extreme overconfidence by default:
- **Hallucination with certainty**: models state false facts in the same confident register as true ones; they do not know what they don't know
- **No calibrated uncertainty**: base LLMs are not trained to produce well-calibrated probabilities; they produce fluent text that sounds authoritative
- **Expert persona amplification**: when prompted to act as an "expert," models become measurably more overconfident and less likely to hedge
- **Chain-of-thought false confidence**: a chain-of-thought that arrives at a conclusion through intermediate steps feels more justified — but each step can introduce error that compounds
- **Missing evidence blindness**: LLMs rarely spontaneously note what information is absent from their analysis

See [[synthesis/sats-for-llm-agents|SATs for LLM Agents]] for SAT-based mitigations.

---

## SATs That Control For This Bias

- **[[concepts/key-assumptions-check|Key Assumptions Check]]** — requires explicitly stating confidence levels for each assumption; surfaces hidden "certainties"
- **[[concepts/quality-of-information-check|Quality of Information Check]]** — directly evaluates whether the information base supports the confidence level being claimed
- **[[concepts/high-impact-low-probability-analysis|High-Impact/Low-Probability Analysis]]** — forces attention onto the distribution tail that overconfidence systematically ignores
- **[[concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses (ACH)]]** — by distributing attention across all hypotheses and their inconsistency scores, prevents false certainty about a single preferred explanation
- **[[concepts/what-if-analysis|What If? Analysis]]** — pre-mortem thinking (assuming failure has occurred) consistently reduces overconfidence by forcing engagement with disconfirming paths

---

## Key References

- Kahneman, D., Slovic, P., & Tversky, A. (Eds.). (1982). *Judgment Under Uncertainty: Heuristics and Biases*. Cambridge University Press.
- Fischhoff, B., Slovic, P., & Lichtenstein, S. (1977). "Knowing with certainty: The appropriateness of extreme confidence." *Journal of Experimental Psychology: Human Perception and Performance*, 3(4), 552–564.
- Kahneman, D. (2011). *Thinking, Fast and Slow*. Farrar, Straus and Giroux. (Chapter 19: "The Illusion of Understanding")
- [[entities/richards-j-heuer-jr|Richards j. heuer jr.]] — *The Psychology of Intelligence Analysis* (1999), Chapter 9

---

## See Also

[[concepts/cognitive-bias|Cognitive Bias]] | [[concepts/anchoring-bias|Anchoring Bias]] | [[concepts/availability-heuristic|Availability Heuristic]] | [[concepts/confirmation-bias|Confirmation Bias]]
