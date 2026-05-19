---
type: concept
tags: [wiki/concept, wiki/bias]
date_updated: 2026-05-19
confidence: high
source_count: 1
---

# Anchoring Bias

The tendency to rely disproportionately on the **first piece of information encountered** (the "anchor") when making subsequent estimates or judgments. Later adjustments from the anchor are systematically insufficient.

---

## Origin

First described by **Amos Tversky** and **Daniel Kahneman** in their seminal 1974 paper "Judgment Under Uncertainty: Heuristics and Biases" (*Science*, 185, 1124–1131). One of the foundational demonstrations of the heuristics-and-biases research program.

Classic experiment: subjects asked to spin a wheel (rigged to land on 10 or 65), then estimate what percentage of African countries are in the UN. Median estimates: 25% (low anchor group) vs. 45% (high anchor group). The wheel result — demonstrably irrelevant — shaped their estimates.

---

## Mechanism

The mind uses the anchor as a starting point and adjusts upward or downward. The adjustment is almost always insufficient — estimates remain closer to the anchor than warranted by the evidence. This persists even when:
- The anchor is known to be arbitrary
- Subjects are warned about anchoring
- Subjects are experts in the domain

---

## Intelligence Analysis Context (per [[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]])

Named directly in the primer's cognitive bias taxonomy:
> "Probability estimates are adjusted only incrementally in response to new information or further analysis."

In analytic practice: anchoring to an initial assessment is one of the most common sources of analytic failure. Once an early judgment is formed (the anchor), subsequent evidence tends to be interpreted as adjustments rather than potential replacements of the original view.

---

## LLM Agentic Systems Context

LLM agents exhibit strong anchoring behavior in multiple dimensions:
- **Prompt anchoring**: the framing of the initial prompt disproportionately shapes all subsequent reasoning
- **Context window anchoring**: the first interpretation of an ambiguous task propagates through the agent's chain-of-thought
- **Prior turn anchoring**: in multi-turn interactions, the agent's own prior output acts as an anchor for its next response
- **Self-consistency anchoring**: agents trained with RLHF show reduced willingness to revise initial outputs, even when shown contradicting evidence

See [[Wiki/synthesis/sats-for-llm-agents|SATs for LLM Agents]] for SAT-based mitigations.

---

## SATs That Control For This Bias

- **[[Wiki/concepts/key-assumptions-check|Key Assumptions Check]]** — forces explicit examination of the initial analytic line as an assumption to be challenged, not a baseline to adjust from
- **[[Wiki/concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses (ACH)]]** — builds all hypotheses simultaneously before evaluating evidence, preventing any single hypothesis from becoming an anchor
- **[[Wiki/concepts/what-if-analysis|What If? Analysis]]** — assumes a different outcome has already occurred, displacing the current estimate as the anchor
- **[[Wiki/concepts/brainstorming|Brainstorming]]** — deferred judgment rule prevents any early idea from becoming an anchor before alternatives are generated

---

## Key References

- Tversky, A. & Kahneman, D. (1974). "Judgment Under Uncertainty: Heuristics and Biases." *Science*, 185(4157), 1124–1131.
- Kahneman, D. (2011). *Thinking, Fast and Slow*. Farrar, Straus and Giroux. (Chapter 11: "Anchors")
- [[Wiki/entities/richards-j-heuer-jr|Richards j. heuer jr.]] — *The Psychology of Intelligence Analysis* (1999), pp. 111–113

---

## See Also

[[Wiki/concepts/cognitive-bias|Cognitive Bias]] | [[Wiki/concepts/confirmation-bias|Confirmation Bias]] | [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]] | [[Wiki/concepts/mind-set|Mind-Set]]
