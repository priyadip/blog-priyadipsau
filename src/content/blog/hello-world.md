---
title: "Template Post — Duplicate Me"
description: "A placeholder template demonstrating math, code, and Markdown features supported by this blog. Not a real post — duplicate this file to write one."
publishDate: 2026-07-12
tags: ["meta", "template"]
draft: true
---

> **This is a template, not a real post.** It exists to demonstrate every
> Markdown/math/code feature this blog supports and to give you a starting
> point. Copy this file to a new slug, replace everything below, and set
> `draft: false` when you're ready to publish. See `WRITING.md` for the full
> workflow.

## Inline math

Attention weights are computed as $\alpha_{ij} = \mathrm{softmax}_j(q_i^\top k_j / \sqrt{d})$,
a normalized dot product between query and key vectors.

## Display math

The scaled dot-product attention output for a single head is:

$$
\mathrm{Attention}(Q, K, V) = \mathrm{softmax}\!\left(\frac{QK^\top}{\sqrt{d_k}}\right)V
$$

## An aligned multi-line block

$$
\begin{aligned}
  \mathcal{L}(\theta) &= -\sum_{i=1}^{n} \log p_\theta(x_i \mid x_{<i}) \\
  \nabla_\theta \mathcal{L}(\theta) &= -\sum_{i=1}^{n} \nabla_\theta \log p_\theta(x_i \mid x_{<i})
\end{aligned}
$$

## A matrix

$$
W = \begin{pmatrix} w_{11} & w_{12} \\ w_{21} & w_{22} \end{pmatrix}
$$

## Code

```python
import torch

def scaled_dot_product_attention(q: torch.Tensor, k: torch.Tensor, v: torch.Tensor) -> torch.Tensor:
    d_k = q.size(-1)
    scores = q @ k.transpose(-2, -1) / d_k**0.5
    weights = torch.softmax(scores, dim=-1)
    return weights @ v
```

## A footnote

Function vectors compose non-additively in the residual stream[^1], which is
part of what motivates this line of work.

[^1]: Placeholder citation — replace with the real reference when this becomes
    an actual post.

## An image reference

<img src="/images/hello-world/diagram.svg" alt="Placeholder diagram — replace with a real figure" width="800" height="450" />

*(This is a stand-in graphic, not a real figure. Explicit `width`/`height` on
the `<img>` tag avoids layout shift — Markdown's `![]()` syntax can't set
those, so use raw HTML when you need them. Add real images under
`public/images/<slug>/`.)*
