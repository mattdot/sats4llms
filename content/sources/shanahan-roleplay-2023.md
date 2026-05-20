---
title: Shanahan, McDonell & Reynolds — Role play with large language models (Nature, 2023)
type: source
tags: [wiki/source]
date_ingested: 2026-05-19
authors: ["Murray Shanahan", "Kyle McDonell", "Laria Reynolds"]
publisher: Nature
publication_id: arXiv:2305.16367 (also Nature)
year: 2023
url: https://arxiv.org/abs/2305.16367
medium: research paper (Nature)
topics: [persona, role-play, anthropomorphism, deception, self-awareness, alignment]
---

# Role play with large language models

**Authors:** Murray Shanahan (DeepMind / Imperial College London), Kyle McDonell, Laria Reynolds
**Venue:** Nature
**Canonical URL:** <https://arxiv.org/abs/2305.16367>

---

## Summary

Foundational theoretical treatment of LLM dialogue agent behavior as **role-play**. Shanahan et al. argue that describing LLM behavior in role-play terms allows us to use familiar folk-psychological vocabulary (deception, self-awareness, persona) without committing to the unwarranted anthropomorphism of treating LLMs as actually having mental states.

The paper directly addresses two phenomena that look concerning under naive framing but become tractable under role-play framing:

1. **Apparent deception** — when an LLM produces output the user believes is false, this is best understood as the model performing a role in which deception is appropriate, not as the model "lying"
2. **Apparent self-awareness** — when an LLM produces output describing its own states or limitations, this is role-play, not introspection

For this wiki, the paper provides the **theoretical vocabulary for [[concepts/persona-capture|persona capture]]**: the phenomenon where assigned roles override the model's underlying training is *exactly* what you'd predict from a role-play framing.

---

## Key Contributions

1. **Reframe LLM behavior as multi-character superposition.** A dialogue agent isn't one character — it's a probability distribution over possible characters consistent with the conversation so far. Each user turn shifts the distribution.
2. **Role-play is the unit of analysis.** Asking "what does the model want?" is the wrong question. Asking "what role is it currently playing, and what would that role do?" is the right one.
3. **Avoids anthropomorphism without dismissing behavior.** The behaviors are real and consequential; the framing just isn't "the AI is conscious."
4. **Implications for safety.** Many alignment concerns (apparent goal-directed deception, apparent self-preservation) become specific role-play scenarios that can be defended against by *not putting the model in those roles*.

---

## Relevance to This Wiki

- **Primary theoretical foundation for [[concepts/persona-capture|Persona Capture]].** Establishes that role-play is the right mental model for what's happening when an LLM "adopts" a persona.
- **Direct relevance to [[synthesis/hypotheses/h4-red-team-mirror-imaging|H4 (Red Team)]].** If red-teaming is implemented by assigning the model an adversary role, the Shanahan framing predicts the failure modes — the model performs *the role of an adversary as humans would expect that role to look*, not an actually-novel adversarial perspective.
- **Critical for [[concepts/mirror-imaging|Mirror Imaging]] mitigation.** Role-play framing implies persona-based mitigations of mirror imaging are themselves subject to mirror imaging — the model performs the role from inside its default value system unless that's also specified.
- **Connects to [[sources/durmus-global-opinions-2023|Durmus 2023]].** Country-conditioning is a role-play assignment; the stereotyping Durmus observes is exactly what the Shanahan framing predicts.

## See Also

- [[concepts/persona-capture|Persona Capture]] · [[concepts/mirror-imaging|Mirror Imaging]]
- [[sources/durmus-global-opinions-2023|Durmus et al. — Global Opinions]] — empirical instance of imperfect role-play
- [[synthesis/hypotheses/h4-red-team-mirror-imaging|H4]] — hypothesis directly implicated
