---
title: Tian et al. — Just Ask for Calibration (2023)
type: source
tags: [wiki/source]
date_ingested: 2026-05-19
authors: ["[[entities/katherine-tian|Katherine Tian]] (et al.)"]
publisher: EMNLP 2023
publication_id: arXiv:2305.14975
year: 2023
url: https://arxiv.org/abs/2305.14975
medium: conference paper
topics: [calibration, overconfidence, verbalized-uncertainty, RLHF, prompting]
---

# Just Ask for Calibration: Strategies for Eliciting Calibrated Confidence Scores from Language Models Fine-Tuned with Human Feedback

**Authors:** Katherine Tian, Eric Mitchell et al. (Stanford)
**Venue:** EMNLP 2023 (camera-ready)
**Canonical URL:** <https://arxiv.org/abs/2305.14975>

---

## Summary

RLHF dramatically degrades the token-probability calibration of language models — RLHF'd models are systematically overconfident in their conditional probabilities. But Tian et al. show that **verbalized confidence — asking the model "how confident are you?" — recovers calibration**, often reducing expected calibration error by ~50% on TriviaQA, SciQ, and TruthfulQA.

The simple intervention is in the title: **just ask**. The information is recoverable; you just have to query for it directly rather than relying on the token logprobs.

---

## Key Findings

1. **RLHF wrecks token-probability calibration.** Base models are well-calibrated; RLHF'd models are not.
2. **Verbalized confidence > logprobs.** For ChatGPT, GPT-4, Claude, asking for confidence in words yields better-calibrated scores than the model's own probabilities.
3. **~50% relative reduction in ECE** on three benchmarks.
4. **Method generalizes across prompting strategies.** Multiple verbalization formats work; the effect is not prompt-specific.

---

## Relevance to This Wiki

- **Direct evidence for [[synthesis/sat-llm-hypotheses|H6]] (What If? reduces overconfidence).** Tian establishes that asking for uncertainty in structured ways works. What If? is a specific structured prompt that should activate the same mechanism.
- **Critical for [[concepts/overconfidence-bias|Overconfidence Bias]].** The bias is fixable by prompt intervention — the information is there.
- **Empirical mirror of [[sources/kadavath-know-2022|Kadavath et al. (2022)]].** Kadavath shows internal self-knowledge exists; Tian shows you can extract it with a simple prompt.
- **Combined with Kadavath, this supports the prompt-engineering protocol approach the wiki takes — SATs as ways to *query for* what the model already knows but doesn't surface.**

## See Also

- [[sources/kadavath-know-2022|Kadavath et al. — Know What They Know (2022)]]
- [[concepts/overconfidence-bias|Overconfidence Bias]]
- [[concepts/hallucination|Hallucination]]
- Lin, Hilton & Evans (2022) *Teaching Models to Express Their Uncertainty in Words* ([arXiv:2205.14334](https://arxiv.org/abs/2205.14334))
- Xiong et al. (ICLR 2024) *Can LLMs Express Their Uncertainty?* ([arXiv:2306.13063](https://arxiv.org/abs/2306.13063))
