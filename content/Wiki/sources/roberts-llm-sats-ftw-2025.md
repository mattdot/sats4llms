---
type: source-summary
tags: [wiki/source]
date_updated: 2026-05-19
source_file: "[[Clippings/roberts-llm-sats-ftw-2025.md]]"
source_date: 2025-05-01
author: "Scott Roberts"
topics: [structured-analytic-techniques, llm-agents, implementation, cybersecurity, tools]
---

# LLM SATs FTW — Scott Roberts

**Author:** [[entities/scott-roberts|Scott Roberts]]  
**Platform:** sroberts.io (personal blog)  
**URL:** https://sroberts.io/posts/llm-sats-ftw/  
**Occasion:** Companion post to a talk at [[entities/sans-emerging-threats-summit|SANS Emerging Threats Summit]] 2025

---

## Summary

A practitioner post by a working cybersecurity analyst who *built and deployed* LLM-assisted tools for three SATs: [[concepts/starbursting|Starbursting]], [[concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses (ACH)]], and [[concepts/key-assumptions-check|Key Assumptions Check]]. The post is notable for being **empirical** — Roberts actually ran the tools on real problems and reports what worked and what didn't, rather than speculating.

Core stance: LLMs are a useful **human-machine team** tool for SATs, not a replacement for analysts. Most valuable for small teams or individual analysts who lack the human capacity to run SATs rigorously.

**Key quote:**  
> "An AI system doesn't have to be better than a human, just better than the best available human." *(attributed to an Ezra Klein Show guest, discussing AI in education)*

---

## Reference Book

Roberts uses [[entities/heuer-pherson-book|Heuer & Pherson (book)]] as his SAT methodology source:  
**Heuer, R.J. Jr. & [[entities/randolph-h-pherson|Randolph H. Pherson]].** *Structured Analytic Techniques for Intelligence Analysis* (3rd ed.). SAGE/College Publishing.  

This is a richer and more comprehensive source than the [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]], which covers only 12 techniques. The Heuer/Pherson book includes additional techniques such as [[concepts/starbursting|Starbursting]].

---

## Architecture (Common to All Three Tools)

- **Frontend:** [Streamlit](https://streamlit.io/) — Python web app framework, no HTML/CSS/JS required
- **Model:** OpenAI GPT-4 (note: author says any model — Gemini, Claude, local — would work)
- **Orchestration:** [LangChain](https://www.langchain.com/)
- **Validation:** [Pydantic](https://docs.pydantic.dev/) — structured output enforcement
- **Pattern:** Each tool takes SAT-specific inputs + OpenAI API key → manages multi-step LLM execution of the SAT process

---

## Experiment 1: Starbursting

**Type:** Idea generation / pre-analysis SAT  
**Implementation:** Zero-shot single query

Process: Submit topic → LLM generates open-ended exploratory questions organized by 5W framework (Who, What, When, Where, Why). Output visualized as a Mermaid mind map.

**Example:** Topic = "ransomware attack on a hospital" → generates questions under each W: Who carried it out? Who was affected? What systems? When detected? Where did it originate? Why was it successful?

**Author's assessment:** Simple to implement; fast; good for scoping a problem.

Live app: https://sat-starburst.streamlit.app/  
Code: https://github.com/sroberts/talk-llm-sats-ftw-code/blob/main/experiment-1-starburst.py

See [[concepts/starbursting|Starbursting]] for technique detail.

---

## Experiment 2: Analysis of Competing Hypotheses (ACH)

**Type:** Diagnostic SAT  
**Implementation:** Multi-step sequential queries (NOT a single zero-shot prompt)

**Multi-step workflow:**
1. Analyst submits initial question (e.g., attribution question)
2. LLM generates list of competing hypotheses
3. LLM generates evidence for and against *each* hypothesis (separate queries per hypothesis)
4. LLM scores each hypothesis-evidence pair on a scale of -5 (strongly against) to +5 (strongly for)
5. Scores are totalled per hypothesis; results output as a ranking table
6. **Human step:** Results exported as CSV; analyst reviews, adds evidence, modifies scores, makes final decision

> *"Technically this isn't a 'few shot' approach, it's actually multiple 'zero shot' queries, but I think of it as a 'few shot' approach because the LLM is generating the queries based on the previous responses."*

**Author's assessment:** "ACH is a complex SAT that takes teams hours or even days to complete... many teams of analysts struggle with it." The LLM approach makes it tractable for small teams. CSV export for human review is critical — LLM handles structure, human handles judgment.

**Implementation note from Roberts:** This is the SAT where the multi-step, stateful approach is essential. A single prompt fails ACH; it requires sequential queries where later queries depend on earlier responses.

Live app: https://sat-ach.streamlit.app/  
Code: https://github.com/sroberts/talk-llm-sats-ftw-code/blob/main/experiment-2-ach.py

---

## Experiment 3: Key Assumptions Check

**Type:** Post-analysis SAT  
**Implementation:** Zero-shot with PDF input processing

Process: Analyst inputs a finished intelligence product (as PDF) → text extracted and chunked → LLM identifies assumptions in each chunk → consolidated list of assumptions returned for analyst review.

**Test case:** Strider report "Inside the Shadow Network: North Korean IT Workers in Russia and Their PRC Backers" (2025) → produced 30 assumptions of "varying quality."

**Technical limitation encountered:**  
> "I ran into a technical limitation of the LLM: too many tokens. I had to break the PDF into chunks, and then ask the LLM to identify the assumptions in each chunk... it shows the issues with relying on LLMs alone."

**Author's assessment:** LLM "did a good job of identifying assumptions, but often missed things that were found in evidence in other parts of the report" — cross-chunk context loss is a real failure mode.

Live app: https://sat-kac.streamlit.app/  
Code: https://github.com/sroberts/talk-llm-sats-ftw-code/blob/main/experiment-3-kac.py

---

## Key Empirical Findings

| Finding | SAT | Implication |
|---------|-----|-------------|
| ACH requires multi-step sequential queries, not a single prompt | ACH | Single-prompt ACH is a failure mode; stateful orchestration is required |
| Key Assumptions Check misses cross-chunk context | KAC | Token-limit chunking causes context fragmentation; cross-reference assumptions across chunks |
| LLMs "help, but rarely replace" human analysts | All | Export + human review step is essential, not optional |
| Chunking required for long documents | KAC | Long-form source analysis needs a map-reduce or sliding-window approach |
| GPT-4 is not required; any capable model works | All | Architecture is model-agnostic |
| Zero-shot works for simple generative SATs (Starbursting) | Starbursting | Simple, bounded, generative tasks need no multi-step orchestration |
| Multi-step is required for evaluative SATs (ACH) | ACH | Evaluation SATs need hypothesis → evidence → scoring as separate passes |

---

## Contradictions and Tensions vs. Existing Wiki

**vs. [[synthesis/sats-for-llm-agents|SATs for LLM Agents]]:**

Our synthesis page proposed ACH as a single multi-hypothesis prompt. Roberts' implementation shows that **effective ACH requires multiple sequential LLM calls** — hypothesis generation, then evidence generation per hypothesis, then scoring per hypothesis — not a single prompt. This is a substantive refinement: our synthesis understated the orchestration complexity required.

**Additional finding not in our synthesis:** Context window chunking for long source documents causes cross-chunk context loss in Key Assumptions Check. Our synthesis did not address this failure mode.

**Agreement:** Both sources converge on the human-machine team model (LLM assists, human reviews) and on the high value of structured output enforcement (Roberts uses Pydantic; our synthesis calls for structured JSON output).

---

## New Entities and Concepts

- [[entities/scott-roberts|Scott Roberts]] — author; cybersecurity analyst, SANS presenter
- [[entities/randolph-h-pherson|Randolph H. Pherson]] — co-author of the primary SAT textbook with Heuer
- [[entities/sans-emerging-threats-summit|SANS Emerging Threats Summit]] — venue for the talk
- [[concepts/starbursting|Starbursting]] — new SAT not in wiki; introduced here

---

## Cross-References

[[concepts/structured-analytic-techniques|Structured Analytic Techniques]] | [[concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses (ACH)]] | [[concepts/key-assumptions-check|Key Assumptions Check]] | [[concepts/starbursting|Starbursting]]  
[[synthesis/sats-for-llm-agents|SATs for LLM Agents]] | [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]
