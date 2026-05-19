---
type: concept
tags: [wiki/concept, wiki/sat]
date_updated: 2026-05-19
confidence: high
source_count: 2
sat_category: diagnostic
---

# Key Assumptions Check

A [[concepts/structured-analytic-techniques|SAT]] that systematically lists and reviews the key working assumptions on which fundamental analytic judgments rest.

---

## Purpose

Make hidden assumptions explicit so they can be examined and challenged. A key assumption is any hypothesis that analysts have accepted as true and which forms the basis of an assessment — often held *unconsciously*.

---

## When to Use

- At the beginning of an analytic project (most useful)
- Before finalizing any judgment
- When rechecking prior assessments
- When a group has worked on an issue long enough that a strong mind-set may have formed

---

## Method (4 Steps)

1. **Review** the current analytic line in writing, for all to see
2. **Articulate** all premises — stated and unstated — that must be true for the analytic line to be valid
3. **Challenge** each assumption: why must it be true? Is it valid under all conditions?
4. **Refine** the list to only those that *must* be true; consider what information would invalidate them

Key questions to ask:
- How confident are we this assumption is correct? Why?
- What circumstances or information might undermine it?
- Is this really a key uncertainty rather than a settled fact?
- Could it have been true in the past but less so now?
- If it proves wrong, would it significantly alter the analytic line?

---

## Value Added

- Exposes faulty logic underlying an analytic argument
- Uncovers hidden relationships between key factors
- Identifies developments that should trigger reassessment
- Prepares analysts for changed circumstances that could otherwise surprise them

---

## Example: DC Sniper Case (2002)

Initial operating assumption: single white male with military training driving a white van. A Key Assumptions Check would have broken this into testable components:

| Assumption | Assessment |
|-----------|-----------|
| Sniper is male | Highly likely but not certain |
| Acting alone | Highly likely but not certain |
| Sniper is white | Likely, but some risk in ruling out nonwhites |
| Has military training | Possible, but insufficient to exclude untrained suspects |
| Driving white van | Credible eyewitness but >70,000 white vans registered in DC suburbs |

The actual sniper was a Black man acting with an accomplice and driving a blue Chevrolet Caprice.

---

## Biases Primarily Controlled

| Bias | How this technique counters it |
|------|-------------------------------|
| [[concepts/anchoring-bias\|Anchoring Bias]] | Forces the *current analytic line* to be written down as an assumption to be challenged, not as the reference point to adjust from |
| [[concepts/confirmation-bias\|Confirmation Bias]] | Making assumptions explicit breaks the unconscious protection mechanism that lets confirmation bias operate invisibly |
| [[concepts/motivated-reasoning\|Motivated Reasoning]] | Requires articulating *why* each assumption must be true; this surfaces motivated premises |
| [[concepts/overconfidence-bias\|Overconfidence Bias]] | Forces assignment of explicit confidence levels to assumptions, revealing hidden certainties |
| [[concepts/status-quo-bias\|Status Quo Bias]] | "The current situation will continue" is made explicit as an assumption rather than remaining a background default |

---

## Applied in Cybersecurity

- **Incident Response**: ensure responders don't base actions on flawed assumptions (e.g., assuming an alert is a false positive) ([[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]])
- **SOC Analysts**: don't prematurely dismiss or prioritize alerts based on faulty logic

---

## LLM Implementation (per [[sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]])

[[entities/scott-roberts|Scott Roberts]] applied KAC to a finished PDF intelligence product — the Strider report on North Korean IT Workers (2025). Implementation:

1. **Input:** Analyst uploads a finished intelligence product (PDF)
2. **Extraction:** PDF text extracted and chunked (required; hits token limits on full documents)
3. **Query per chunk:** LLM identifies assumptions in each text chunk
4. **Consolidation:** Assumptions from all chunks are merged and deduplicated

**Result:** ~30 assumptions extracted of "varying quality."

**⚠ Known failure mode — cross-chunk context loss:**  
> *"The LLM did a good job of identifying assumptions, but often missed things that were found in evidence in other parts of the report."*  
Chunking prevents the model from cross-referencing assumptions against evidence scattered across the document. A sliding-window or map-reduce approach may reduce this; full document summarization first may also help.

**Architecture:** Streamlit + GPT-4 + LangChain + Pydantic  
Live app: https://sat-kac.streamlit.app/ | Code: https://github.com/sroberts/talk-llm-sats-ftw-code/blob/main/experiment-3-kac.py

---

## Sources

- [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] (pp. 7–9)
- [[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]]
- [[sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]
