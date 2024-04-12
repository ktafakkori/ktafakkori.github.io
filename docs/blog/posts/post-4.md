---
draft: False 
title: "MINLP to MILP: How does linearization work?"
date: 2024-04-12
categories:
  - Optimization
  - Python
  - Modules
authors:
  - ktafakkori
slug: linearization-minlp-milp
comments: true
---

It is tempting to linearize a non-linear relationship among decision variables to make our model suitable for a MILP solver. But is it worth it?

<!-- more -->

Here, you can see the impact of piece-wise linearization using FelooPy 0.3.0's linearization module. We wish to minimize x**2, where x is a free variable.

The procedure is to consider a bound for this free variable. The first problem is that we are almost always unaware of the best possible bounds to consider (as we don't actually know where the optimal variable lies), and sometimes, such bounds cannot be determined easily. The second problem is evident in the attached test results.

We should consider around 1000 breakpoints (or lower) for this single variable to ensure that the objective function is computed precisely (due to the impact of the intercepts). If we rely on the assumption that PLA focuses on approximation, what if it is unacceptable in a business setting, i.e., when it is equivalent to the investment amount? Besides, with how many breakpoints can we ensure the desired accuracy?

On the other hand, we consider a single variable x. What if there are more variables? What would be the overall computational burden?

In this simple example, the CPT was 4.74e3 microseconds for ten breakpoints (20 constraints and nine binary and positive variables), 5.23e4 microseconds for 100 breakpoints (200 constraints and 99 binary and positive variables), and 2.19e6 for 1000 breakpoints (2000 constraints and 999 binary and positive variables), which exponentially increases.

In summary, if you want to solve an unconstrained problem like minimizing x**2 precisely using a MILP solver, you would need 2000 constraints and 999 binary and positive variables!

```py
# Code
m.lin_approx(name="x", f=lambda x:x**2, var=x, bound=[-10,10], num_breakpoints=10)

# num_breakpoints=10

┌─ Model ────────────────────────────────────────────────────────────────────────────────┐
│                       B       I       P       F       E       S       O       C        │
╞════════════════════════════════════════════════════════════════════════════════════════╡
│ Class                 1       0       1       1       0       0       1       1        │
│ Size                  9       0       9       1       0       0       1       20       │
└────────────────────────────────────────────────────────────────────────────────────────┘

┌─ Metric ────────────────────────────────────────────────── 00:00:00 h:m:s 4.74e+03 μs ─┐
│                                                                                        │
│ Objective                                                                     1.23     │
│                                                                                        │
└────────────────────────────────────────────────────────────────────────────────────────┘

# num_breakpoints=100

┌─ Model ────────────────────────────────────────────────────────────────────────────────┐
│                       B       I       P       F       E       S       O       C        │
╞════════════════════════════════════════════════════════════════════════════════════════╡
│ Class                 1       0       1       1       0       0       1       1        │
│ Size                  99      0       99      1       0       0       1       200      │
└────────────────────────────────────────────────────────────────────────────────────────┘

┌─ Metric ────────────────────────────────────────────────── 00:00:00 h:m:s 5.23e+04 μs ─┐
│                                                                                        │
│ Objective                                                                     0.01     │
│                                                                                        │
└────────────────────────────────────────────────────────────────────────────────────────┘

# num_breakpoints=1000

┌─ Model ────────────────────────────────────────────────────────────────────────────────┐
│                       B       I       P       F       E       S       O       C        │
╞════════════════════════════════════════════════════════════════════════════════════════╡
│ Class                 1       0       1       1       0       0       1       1        │
│ Size                  999     0       999     1       0       0       1       2000     │
└────────────────────────────────────────────────────────────────────────────────────────┘

┌─ Metric ────────────────────────────────────────────────── 00:00:02 h:m:s 2.19e+06 μs ─┐
│                                                                                        │
│ Objective                                                                     0.00     │
│                                                                                        │
└────────────────────────────────────────────────────────────────────────────────────────┘


```