---
draft: False 
title: "Practical versus Theoretical Operations Research"
date: 2024-03-05
categories:
  - Optimization
  - Challenges
  - Practical
authors:
  - ktafakkori
slug: operations-research-theory-practice
comments: true
---

# Practical versus Theoretical Operations Research

Four challenging but realistic aspects differentiate applied operations research from theoretical operations research:

<!-- more -->


1) The real-world problems are inherently multi/many-objective. When considering only one objective, we consider only one aspect of many in decision-making, making the obtained solution sub-optimal or neglecting the impact of other indicators.


2) The real-world problems are inherently solved based on data, which makes inputs and outputs uncertain, even if estimated or predicted. Hence, the "quality" of proposed solutions is subject to the uncertainty-handling techniques we use.


3) The real-world problems are barely modelable or completely non-linear. We usually have billions of decision variables in practice. If the scale increases, we might even need to rethink the model, as the solutions might become unreliable regarding their logicality. Besides, the proposed models only work if an expert's "assumed aspects" are met.


4) Assume the day we have computers that handle computationally complex NP-Hard problems in seconds! So solving combinatorial optimization problems even using a basic branch and bound technique is not taking long, without the need for special pricing, checking, or cutting heuristic, or even those meta-heuristic algorithms! Still, our models, specially those involve complex mathematical relations among decision variables remain unsolvable in an "exact" manner.
