---
id: w04-cgao19-lasso-zero-meaning
title: "What is a lasso zero actually evidence of?"
author: cgao19
---

Soft thresholding makes $\hat{\beta}_j$ exactly zero whenever $|a_j| \le \lambda$, so sparsity is a property of the minimizer, not of numerical rounding. But the correlated-predictor example shows that one member of a correlated pair can enter the model while its partner is dropped, and that a different sample or fold assignment can reverse which one survives.

This makes me unsure what a zero licenses me to say. If I tune with the one-standard-error rule, I accept a larger $\lambda$ and therefore more zeros on purpose, because the extra error is small. Those additional zeros were bought for parsimony, not because the data said those variables are unrelated to the response.

So when a variable is dropped, can we separate three causes: its signal is weak relative to $\lambda$, a correlated substitute absorbed it, or the one-standard-error rule traded it away? Is there something we can report next to a lasso fit, such as selection frequency across resamples, the full path, or an elastic-net refit, that distinguishes them? Or should a zero never be reported as a claim about the variable itself?
