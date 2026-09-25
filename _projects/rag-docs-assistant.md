---
title: RAG Docs Assistant
summary: A retrieval-augmented Q&A assistant over FastAPI's docs, with a retrieval eval comparing two chunking strategies.
learning_path: 1
tech:
  - Claude
  - Python
  - Chroma
  - sentence-transformers
link: https://github.com/DaleShockley/rag-docs-assistant
---

**Step 1 of my AI learning path: build a RAG system and measure its retrieval.**

Ask a plain-English question about FastAPI and get an answer grounded in the actual docs, with a citation to the source file. A local, free embedding model finds the relevant chunks, and Claude reads them and writes the answer.

The point was to treat chunking as a real design decision rather than a default. I wrote 15 questions, each tied to the doc that should answer it, and scored two chunking strategies on whether the right doc came back:

| Strategy | Hit rate @3 | Hit rate @5 |
|---|---|---|
| Fixed-size (800 chars, 100 overlap) | 15/15 | 15/15 |
| Header-aware (split on headings) | 14/15 | 15/15 |

The "smarter" header-aware chunking lost at k=3. These docs have many short subsections, so some chunks were too small to carry the keywords a question needed.

**What the next project taught me about this one:** the eval checks whether the right *file* comes back. Later, grading the actual answers ([step 3](/projects/grounded-answer-judge/)) showed the assistant still fell short on 4 of 26 questions, because the right file came back but not the right *section*. A perfect retrieval score was hiding real misses.
