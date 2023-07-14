---
title: "Benders decomposition algorithm: Why is it important?"
date: 2022-11-25
draft: false
aliases: ["/why-is-novel-metaheuristic-algorithm-development-often-criticized/"]
---
_Most of the heuristic optimization algorithms proposed are repetitive or follow the same principle/structure._

New research in the heuristic optimization field is often fastly criticized due to some weak studies in the field. According to [Sörensen (2013)](https://onlinelibrary.wiley.com/doi/abs/10.1111/itor.12001), while truly innovative research of high quality is STILL being performed, multiple reasons do exist that make a new contribution worthless:

- Using a different word for the same old concept (renaming), leading to the reiteration of existing knowledge. To avoid this, we should not change the standard vocabulary of this context. It is better to separate our "inspiration" from "theoretical algorithm development" or the report of results and discussions" to avoid this. For instance, through the stages of algorithm development, use "search agent" or "solution" instead of the metaphor elements (e.g., crow, harmony, ...). Similarly, use "better objective value (fitness)", "decision variable", and so on. It not only avoids repetition of existing knowledge but helps to understand the algorithm easier.
- Developing similar search operators even though the metaphor is different. This case is similar to when we apply the same approach to a different situation. If so, we must compare the results where possible. Accordingly, we should not leave the readers to find the linkage of our approach with previous studies.
- Not explaining similarities if the metaphor does the same behavior as the others or other studies. For instance, if the behavior of a "novel" meta-heuristic algorithm is similar to a reinforcement learning algorithm, we should state and explain this.

In summary, the paper of [Sörensen (2013)](https://onlinelibrary.wiley.com/doi/abs/10.1111/itor.12001), alludes to a necessary research principle, which is "we should always rigorously position our research in the literature by fair unbiased comparisons". We should not be obsessed to propose a novel method or multiple contributions, but more be focused on links. For instance, we should also show similarities to our method/approach and try not to focus on showing our contribution is way better. If a contribution is really novel, we should strongly prove or demonstrate it by rigorous comparisons. For instance, by statistical validations or well-known test problems.

Herein, I summarize a high-quality algorithm development instruction discussed by [Sörensen (2013)](https://onlinelibrary.wiley.com/doi/abs/10.1111/itor.12001):
Adequately framing a method entails explaining it using general optimization terminology (not metaphor-based language):

1. deconstructing it and showing its components
2. determining similar components with previous studies (if any)
3. how these components are adapted to (or do work in) the optimization process
4. transparently doing parameter-tuning (if any).
