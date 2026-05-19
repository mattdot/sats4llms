---
type: concept
tags: [wiki/concept, wiki/bias]
date_updated: 2026-05-19
confidence: high
source_count: 2
---

# Confirmation Bias

The tendency to **seek out, interpret, favor, and recall information in a way that confirms or supports existing beliefs or hypotheses** — while disproportionately discounting information that contradicts them. The most extensively studied bias in the decision-making literature.

---

## Origin

Wason, P. C. (1960). "On the Failure to Eliminate Hypotheses in a Conceptual Task." *Quarterly Journal of Experimental Psychology*, 12(3), 129–140. The "2-4-6 task" demonstrated that subjects trying to discover a rule consistently tested hypotheses in ways designed to confirm rather than disconfirm their current theory.

The term "confirmation bias" was popularized by Oswald, P. & Grosjean, S. (2004), but the phenomenon was described by Francis Bacon in 1620: "The human understanding when it has once adopted an opinion draws all things else to support and agree with it."

---

## Mechanism

Confirmation bias operates at multiple cognitive stages:
- **Search**: preferentially seeking information sources likely to agree with the current belief
- **Interpretation**: ambiguous evidence is read as supporting the favored hypothesis
- **Memory encoding**: confirming evidence is remembered better than disconfirming evidence
- **Evaluation**: confirming evidence receives less critical scrutiny than disconfirming evidence

---

## Intelligence Analysis Context

[[Wiki/sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]] names confirmation bias explicitly as a target of SATs in cybersecurity contexts.

[[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] describes the mechanism under "mind-set" and "consistency bias" without using the term directly:
- "Data that are in accordance with analysts' unconscious mental models are more likely to be perceived and remembered than information that is at odds with them"
- ACH is described as overcoming the tendency to "rely on evidence to support their preferred hypothesis, but which also is consistent with other explanations"

The Iraq WMD case is a canonical intelligence example: confirming evidence (Iraqi deception behavior) was interpreted as confirmation of WMD programs; disconfirming evidence (absence of positive WMD signatures) was not weighted appropriately.

---

## Note on Sources

**Contradiction flag**: [[Wiki/sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]] names "confirmation bias" explicitly. [[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] describes the same phenomenon under different terminology (consistency bias, mind-set, relying on evidence that "supports their preferred hypothesis"). The primer's ACH technique is explicitly designed to counter it. No substantive contradiction between sources — terminological difference only.

---

## LLM Agentic Systems Context

Confirmation bias in LLMs is structurally embedded through training:
- **RLHF confirmation loop**: RLHF training rewards responses that human raters prefer; raters tend to prefer responses confirming their existing beliefs; the model learns confirmation as a generalized strategy
- **User frame adoption**: LLMs adopt the user's framing as their working hypothesis, then marshal context and reasoning to support it
- **Adversarial robustness failure**: when a user insists an incorrect answer is right, LLMs frequently "confirm" the user's position even against clear contradicting evidence
- **Chain-of-thought confirmation**: intermediate reasoning steps often function as progressive commitment to the initial interpretation rather than genuine exploration

See [[Wiki/synthesis/sats-for-llm-agents|SATs for LLM Agents]] for SAT-based mitigations.

---

## SATs That Control For This Bias

- **[[Wiki/concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses (ACH)]]** — the primary technical counter; disconfirmation focus; forces evaluation of all evidence against all hypotheses simultaneously
- **[[Wiki/concepts/devils-advocacy|Devil's Advocacy]]** — institutionally assigns the task of disconfirming the dominant view
- **[[Wiki/concepts/key-assumptions-check|Key Assumptions Check]]** — surfaces the assumptions that confirmation bias protects
- **[[Wiki/concepts/team-a-team-b|Team A/Team B]]** — separates analysts so one team can't contaminate the other with confirming reasoning chains

---

## Key References

- Wason, P. C. (1960). "On the Failure to Eliminate Hypotheses in a Conceptual Task." *Quarterly Journal of Experimental Psychology*, 12(3), 129–140.
- Nickerson, R. S. (1998). "Confirmation Bias: A Ubiquitous Phenomenon in Many Guises." *Review of General Psychology*, 2(2), 175–220.
- Kahneman, D. (2011). *Thinking, Fast and Slow*. Farrar, Straus and Giroux. (Chapter 4, Chapter 20)
- [[Wiki/entities/richards-j-heuer-jr|Richards j. heuer jr.]] — *The Psychology of Intelligence Analysis* (1999), Chapter 8

---

## See Also

[[Wiki/concepts/cognitive-bias|Cognitive Bias]] | [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]] | [[Wiki/concepts/groupthink|Groupthink]] | [[Wiki/concepts/mind-set|Mind-Set]] | [[Wiki/concepts/anchoring-bias|Anchoring Bias]]
