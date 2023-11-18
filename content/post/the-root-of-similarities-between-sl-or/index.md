---
title: "The root of similarities between supervised learning and operations research"
date: 2022-07-15
draft: false
image: post-image.png
math: true
aliases: ["/the-root-of-similarities-between-sl-or/"]
---
In this short article, I am sharing my opinion and explaining how operations research and machine learning are interrelated.

Suppose a continuous facility location problem with squared Euclidean distance as follows:

$$
\begin{aligned}
  & \min && \sum\limits_{t = 1}^{\left| T \right|}w_t\lVert\bf{g}-\bf{b_t}\rVert^2 \\
  &&& {\bf{g}} \in \mathbb{R^{|U|}} \\
  \end{aligned}
$$

If you remember, the distance (similarity) measure applied in this facility location problem helps find the location of emergency facilities. That means we want to find the location of a single facility that can serve _T_ facilities as fast as possible. As seen, _g_ is in bold format and not indexed. Being in the boldface means that _g_ has other dimensions (a common mathematical notation). For example, since this is a continuous facility location problem, we need to find $g_1$ and $g_2$ indicating $x$ and $y$ of a new facility in a two-dimensional space. $b_t$, which is also in bold format, denotes _x_ and _y_ for the _t_-th existing facility. Finally, $w_t$ is the weight of from-to flows between existing and the new facilities (a similarity indicator). Now consider the following optimization problem:

$$
\begin{aligned}
  & \min && \sum\limits_{t = 1}^{\left| T \right|}w_t\lVert g_t-b_t \rVert^2 \\
  &&& g_t \in \mathbb{R} \\
  \end{aligned}
$$

In this optimization problem, we wish to find values $g_t$ close to $b_t$, which are not bold, meaning that they have no other dimensions. But, $g$ is now indexed by $t$. Contrary to the previous model, we need to find the location of $t$ new facilities close to the $t$ existing facilities. If we do not consider some extra constraints, $g_t$ would become equal to $b_t$. This means we establish all $t$ new facilities on the existing $t$ facilities to reduce their distance.

In machine learning (specifically supervised learning), existing facilities are represented by data points (observations), and $g_t$ is the location of new $t$ data points, which we wish to be close to $b_t$ (existing facilities). However, without constraints, the machine does not learn anything! We want to find a single function (instead of a single facility) that can be applied to all data points. Accordingly, the optimization model becomes:

$$
\begin{aligned}
  & \min && \sum\limits_{t = 1}^{\left| T \right|}w_t\lVert g_t-b_t \rVert^2 \\
  &&& g_t = y_t \quad \forall t \in T \\
  &&& y_t = \sum_{i=1}^{|I|} a_{ti}x_i + z \quad \forall t \in T \\
  &&& g_t, y_t, x_i, z \in \mathbb{R} \\
  \end{aligned}
$$

where the first and second constraints represent post- and pre-activation functions, respectively.

This optimization problem is called linear regression, the basis for all machine learning models and algorithms! Note that $w_t$ here should equal one (or better 1/T) as we do not want to make a biased model!
