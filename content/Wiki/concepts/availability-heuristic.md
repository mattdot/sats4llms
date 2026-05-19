---
type: concept
tags: [wiki/concept, wiki/bias]
date_updated: 2026-05-19
confidence: high
source_count: 1
---

# Availability Heuristic

The tendency to judge the **probability or frequency of an event based on how easily examples come to mind** — i.e., how cognitively "available" they are. Vivid, recent, or emotionally salient events are overweighted; mundane, statistical, or abstract events are underweighted.

---

## Origin

Tversky & Kahneman (1973), "Availability: A Heuristic for Judging Frequency and Probability," *Cognitive Psychology*, 5(2), 207–232.

Classic demonstration: which is more common in English — words starting with "r" or words with "r" as the third letter? Most people say words starting with "r" because they are easier to retrieve (more "available"). In fact, words with "r" third are more common. The ease of retrieval substituted for the actual frequency.

---

## Mechanism

The mind uses retrieval ease as a proxy for frequency or probability. This produces systematic errors:
- **Recency effect** — recent events are overweighted relative to base rates
- **Salience effect** — dramatic or emotionally loaded events feel more probable than they are
- **Personal experience effect** — events you've witnessed personally are weighted more than equivalent statistical evidence
- **Media coverage effect** — heavily covered events (plane crashes, shark attacks) are judged more probable than underreported ones (car accidents, heart disease)

---

## Intelligence Analysis Context (per [[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]])

Named in the primer's probability-estimation bias taxonomy:
> "Probability estimates are influenced by how easily one can imagine an event or recall similar instances."

Analytic implication: analysts who have personally witnessed or intensively studied a particular type of threat may overestimate its probability in future situations where base rates argue otherwise. The failure mode of the availability heuristic in intelligence: **analogical reasoning** — "this looks like X, and X happened, so this will probably end the same way" — when the analogy may not hold.

---

## LLM Agentic Systems Context

Availability is deeply embedded in how LLMs work:
- **Training corpus frequency bias**: events, entities, and patterns that appear frequently in the training corpus are "more available" to the model — they are retrieved more easily and with higher confidence
- **Recency in context window**: tokens and reasoning steps near the end of the context window are more influential on next-token predictions than distant context (analogous to recency availability)
- **Sycophancy as availability**: the most "available" response pattern for an RLHF-trained LLM is often agreeing with the user's framing — it was rewarded most frequently during training
- **Hallucination pattern**: when a model lacks knowledge, it substitutes a plausible-sounding pattern from similar but different training examples — availability substituting for accuracy

See [[Wiki/synthesis/sats-for-llm-agents|SATs for LLM Agents]] for SAT-based mitigations.

---

## SATs That Control For This Bias

- **[[Wiki/concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses (ACH)]]** — requires explicitly listing *all* hypotheses including those that don't readily come to mind; the matrix structure surfaces low-availability alternatives
- **[[Wiki/concepts/high-impact-low-probability-analysis|High-Impact/Low-Probability Analysis]]** — specifically designed to force attention onto events that are low-availability precisely because they are infrequent
- **[[Wiki/concepts/alternative-futures-analysis|Alternative Futures Analysis]]** — generates scenarios through systematic variation of drivers rather than memory retrieval
- **[[Wiki/concepts/quality-of-information-check|Quality of Information Check]]** — separates "what we know" from "what we remember" by reviewing the full source record
- **[[Wiki/concepts/outside-in-thinking|Outside-In Thinking]]** — expands the frame to include factors outside the analyst's immediate experience base

---

## Key References

- Tversky, A. & Kahneman, D. (1973). "Availability: A Heuristic for Judging Frequency and Probability." *Cognitive Psychology*, 5(2), 207–232.
- Kahneman, D. (2011). *Thinking, Fast and Slow*. Farrar, Straus and Giroux. (Chapter 12: "The Science of Availability")
- [[Wiki/entities/richards-j-heuer-jr|Richards j. heuer jr.]] — *The Psychology of Intelligence Analysis* (1999), pp. 114–115

---

## See Also

[[Wiki/concepts/cognitive-bias|Cognitive Bias]] | [[Wiki/concepts/anchoring-bias|Anchoring Bias]] | [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]] | [[Wiki/concepts/confirmation-bias|Confirmation Bias]]
