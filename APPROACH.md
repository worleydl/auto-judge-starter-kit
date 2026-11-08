SLM Baselines
---

## Approach

The SLM baselines seek to establish benchmarks for a less computationally expensive approach compared to LLM's.  The goal was to see how the latest SLM/LLM models perform against each other.

The `problem_statement` and the individual citation sentences from the `responses` were embedded in hyperspace.  The cosine similarity (or equivalent) was computed for each submission using the embeddings.  Evaluations were run against the following models:

- MiniLM (biencoder)
- msmarco (biencoder)
- msmarco-mini-lm (crossencoder)

To generate the final ranking, the sim scores for each submission's `problem_statement`/`sentence` were averaged and then sorted.

## Results

Early evaluations from legacy data suggest low correlation to the human judged results.  Future iteration with more relevance signals or different embedding strategies should at least get in the ballpark with only anomalies slipping thru.

Signal ideation:
- Traditional BM25 or other term frequency based scoring
- Bring in data from the cited documents to compare against the `problem_statement`
- Make use of other metadata if applicable

## Other Thoughts

Embeddings provide a powerful relevance signal but tend to let false positives slip thru.  On the other hand, a low cosine sim score is typically a strong signal of a true negative.  To balance out this approach a counterbalance signal of true positives is required and should be blended to generate the final score.
