---
title: Grounded Answer Judge
summary: An LLM-as-judge for RAG answers, tested against human labels, seeded flaws and bias probes, then used to pick which model writes the answers.
learning_path: 3
tech:
  - Claude
  - LLM-as-judge
  - Evals
  - GitHub Actions
link: https://github.com/DaleShockley/grounded-answer-judge
---

**Step 3 of my AI learning path: measure answer quality, and find out when an AI grader can be trusted.**

The judge grades each answer from my [RAG assistant](/projects/rag-docs-assistant/) on three things: is it **faithful** to the retrieved docs, is it **relevant** to the question, and is it **cited correctly**. The hard part wasn't building the judge. It was proving how far to trust it.

**What I built:** 47 answers to grade (30 real, plus 17 with a single deliberate flaw each), a written rubric, a blind labeling page, the judge itself, and scoring for agreement, consistency across repeated runs, and bias. Then I used the judge to compare four Claude models as the answer writer, and added a CI gate that fails if the judge or the answers get worse.

| Result | |
|---|---|
| Seeded flaws the judge caught | 17/17, every run |
| Rubric judgment calls | 5/9 → 8–9/9 after writing the rubric into the prompt (same model) |
| Same verdict across 3 identical runs | 95% |
| Swayed by longer answers or confident tone | No |
| Answer models compared | Quality tied; switched the default to the one 25% cheaper and 40% faster |
| A "be more generous" prompt edit | Caught by the CI gate (14/17 flaws, 4/9 rubric) |

**The lesson I didn't expect: my own labels needed checking too.** My first blind labeling pass caught only 6 of the 17 planted flaws. I graded each answer as a whole instead of on three separate criteria. Then, when I reviewed my disagreements with the judge's reasoning on screen, I sided with it 46 times out of 48. That's automation bias, and it made my "after" agreement numbers partly circular. So I kept both passes, reported the caveat, and scored the judge on cases whose right answer doesn't depend on any grader.

Everything is written up, with 35 lessons each tied to a measured result, in the repo's [LESSONS_LEARNED.md](https://github.com/DaleShockley/grounded-answer-judge/blob/main/LESSONS_LEARNED.md). The whole project cost about $4 in API usage.
