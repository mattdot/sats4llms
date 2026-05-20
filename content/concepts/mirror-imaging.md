---
type: concept
tags: [wiki/concept, wiki/bias]
date_updated: 2026-05-19
confidence: high
source_count: 2
---

# Mirror Imaging

The tendency to **assume that adversaries, foreign actors, or other agents think, value, and make decisions the same way the analyst does**. In psychology: the Fundamental Attribution Error applied cross-culturally and cross-institutionally.

---

## Origin and Names

**Fundamental Attribution Error** (Ross, 1977): the general cognitive bias of attributing others' behavior to their character/nature while attributing one's own behavior to situational factors.

**Mirror Imaging** is the intelligence community's term for the specific manifestation: analysts project their own decision-making frameworks onto foreign actors, assuming rational calculation matches their own rationality norms, risk tolerances, and value hierarchies.

Named in [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]'s causality bias taxonomy:
> "Behavior of others is attributed to some fixed nature of the person or country, while our own behavior is attributed to the situation in which we find ourselves."

---

## Intelligence Analysis Context

Mirror imaging produces systematic failures in adversary analysis:
- **Rationality projection**: assuming adversaries weigh costs/benefits as the analyst would; missing that an adversary may have different values, time horizons, or risk tolerance
- **Motivation blindness**: failing to consider that an action that would be irrational for "us" may be rational given the adversary's constraints and goals
- **Historical examples**: analysts consistently underestimated Soviet willingness to take aggressive action because the risk seemed unacceptable by Western rationality norms (Cuban Missile Crisis is partly a mirror imaging failure in the opposite direction — Khrushchev's belief the US would accept a fait accompli)

---

## LLM Agentic Systems Context

LLMs exhibit a specific form of mirror imaging rooted in their training:
- **Value alignment projection**: LLMs trained on human feedback project the values of their RLHF raters onto all users and all modeled agents — they assume universally "reasonable" goals
- **User perspective capture**: agents frequently adopt the user's framing as the correct framing without stepping back to consider whether the user's mental model is accurate
- **Persona collapse**: agents asked to roleplay or model adversarial actors often sanitize or rationalize the adversary's behavior through the agent's own value system
- **Homogeneity in multi-agent systems**: multiple instances of the same model "mirror image" each other, producing echo chambers rather than genuine independent analysis

See [[synthesis/sats-for-llm-agents|SATs for LLM Agents]] for SAT-based mitigations.

---

## SATs That Control For This Bias

- **[[concepts/red-team-analysis|Red Team Analysis]]** — directly and structurally requires adopting the adversary's perspective; the entire technique exists to counter mirror imaging
- **[[concepts/outside-in-thinking|Outside-In Thinking]]** — expands the frame beyond the analyst's natural reference point to include external constraints and logics
- **[[concepts/alternative-futures-analysis|Alternative Futures Analysis]]** — generates scenarios driven by adversary logic, not analyst preferences
- **[[concepts/devils-advocacy|Devil's Advocacy]]** — builds the strongest possible case from a different set of premises

---

## Key References

- Ross, L. (1977). "The intuitive psychologist and his shortcomings: Distortions in the attribution process." In L. Berkowitz (Ed.), *Advances in Experimental Social Psychology*, Vol. 10, pp. 173–220. Academic Press.
- Heuer, R. J. Jr. (1999). *The Psychology of Intelligence Analysis*, Chapter 4: "Strategies for Analytical Judgment." [[entities/richards-j-heuer-jr|Richards j. heuer jr.]]
- Chang, W., et al. (2018). "Lessons from the Intelligence Community on Improving Forecasting." *Perspectives on Psychological Science*.
- [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] — attribution bias in causality taxonomy

---

## Empirical Evidence (LLM)

| Study | Finding |
|---|---|
| [[sources/durmus-global-opinions-2023\|Durmus et al. (2023)]] | LLM default responses align most with USA / Western European opinions (GlobalOpinionQA benchmark, derived from Pew + World Values Survey). Country-conditioning shifts opinion but introduces stereotyping. Translation alone does not shift opinion alignment. |

**Implication for SATs:** [[concepts/red-team-analysis\|Red Team]] and [[concepts/outside-in-thinking\|Outside-In Thinking]] in an LLM context are operating on top of WEIRD priors. Persona prompts work imperfectly. Adversary modeling tends to produce sanitized Western-flavored adversaries by default. See [[synthesis/sat-llm-hypotheses\|H4]].

---

## Case Studies

- **Iraq WMD 2003.** The Kerr Report (cited in [[sources/grey-dynamics-intelligence-failure-2024|Grey Dynamics 2024]]) found US satellite imagery analysis "failed to acknowledge the political/cultural context" of Saddam's actions — a direct instance of mirror imaging at the collection-strategy level. US intelligence had **zero HUMINT sources in Iraq from 1998–2003**, meaning analysis ran on overhead imagery interpreted through Western assumptions about a leader operating with very different incentives and information.

## See Also

[[concepts/cognitive-bias|Cognitive Bias]] | [[concepts/groupthink|Groupthink]] | [[concepts/motivated-reasoning|Motivated Reasoning]] | [[concepts/red-team-analysis|Red Team Analysis]]
