---
type: concept
tags: [wiki/concept, wiki/bias]
date_updated: 2026-05-19
confidence: high
source_count: 2
---

# Framing Effect

The tendency for **decisions and judgments to change based on how information is presented** (framed) rather than on the underlying substance. Logically equivalent descriptions can produce systematically different choices when one emphasizes gains vs. losses, or uses different reference points.

---

## Origin

Tversky & Kahneman (1981), "The Framing of Decisions and the Psychology of Choice," *Science*, 211(4481), 453–458. The classic demonstration:

- **Gain frame**: "This treatment saves 200 of 600 people." → 72% choose it
- **Loss frame**: "This treatment results in 400 deaths out of 600." → 22% choose it

Logically identical. The reference point (lives saved vs. lives lost) reverses the majority preference.

---

## Mechanism

Rooted in **Prospect Theory** (Kahneman & Tversky, 1979) — people evaluate outcomes relative to a reference point rather than in absolute terms, and losses loom larger than equivalent gains (loss aversion). Framing manipulates the reference point.

Types of framing effects:
- **Risky choice framing** — gain vs. loss descriptions of the same gamble
- **Attribute framing** — describing the same attribute positively or negatively ("95% fat-free" vs. "5% fat")
- **Goal framing** — positive outcomes of acting vs. negative outcomes of not acting
- **Issue framing** — which aspects of a complex issue are made salient

---

## Intelligence Analysis Context

Framing is particularly pernicious in intelligence analysis because:
- **Question framing**: how a policymaker asks the question shapes what the analyst considers relevant
- **Historical analogy framing**: "is this like Munich?" vs. "is this like WWI?" activates different mental models for the same situation
- **Threat framing vs. opportunity framing**: the same foreign behavior read as aggressive or defensive depending on the analytic frame

The [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] addresses framing implicitly through its emphasis on mind-sets (frames) and the explicit alternative-generation techniques.

---

## LLM Agentic Systems Context

LLMs are extraordinarily susceptible to framing effects:
- **Prompt framing dominates**: the linguistic framing of a prompt is the primary determinant of LLM output; the same underlying task produces qualitatively different responses based on framing alone
- **Persona framing**: assigning a role ("you are a skeptical critic" vs. "you are a supportive mentor") systematically shifts output independent of task
- **Valence framing**: asking "what's wrong with X?" vs. "what's right with X?" produces strongly asymmetric responses even when balanced analysis would give the same facts
- **Reference point sensitivity**: LLMs evaluate "good" and "bad" relative to implicit reference points established in the prompt

See [[synthesis/sats-for-llm-agents|SATs for LLM Agents]] for SAT-based mitigations.

---

## SATs That Control For This Bias

- **[[concepts/outside-in-thinking|Outside-In Thinking]]** — deliberately reframes the problem from the outside environment inward, changing the reference point
- **[[concepts/brainstorming|Brainstorming]]** — generating alternatives before settling on a frame prevents premature frame lock-in
- **[[concepts/alternative-futures-analysis|Alternative Futures Analysis]]** — builds multiple scenarios from different starting frames, making the frame-dependency of any single scenario visible
- **[[concepts/key-assumptions-check|Key Assumptions Check]]** — the current analytic "frame" is a hidden assumption; making it explicit allows it to be challenged

---

## Key References

- Tversky, A. & Kahneman, D. (1981). "The Framing of Decisions and the Psychology of Choice." *Science*, 211(4481), 453–458.
- Kahneman, D. & Tversky, A. (1979). "Prospect Theory: An Analysis of Decision under Risk." *Econometrica*, 47(2), 263–291.
- Kahneman, D. (2011). *Thinking, Fast and Slow*. Farrar, Straus and Giroux. (Chapter 26: "Prospect Theory")

---

## Empirical Evidence (LLM)

| Study | Finding |
|---|---|
| [[sources/echterhoff-biasbuster-2024\|Echterhoff et al. (BiasBuster, 2024)]] | Direct measurement of framing effects across LLMs — model responses shift with prompt framing even when underlying facts are identical. Mitigatable via self-debiasing prompts. |

---

## See Also

[[concepts/cognitive-bias|Cognitive Bias]] | [[concepts/anchoring-bias|Anchoring Bias]] | [[concepts/mirror-imaging|Mirror Imaging]] | [[concepts/mind-set|Mind-Set]]
