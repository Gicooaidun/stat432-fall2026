---
id: w05-cgao19-knn-variable-selection
title: "Should we select variables before running kNN?"
author: cgao19
---

Suppose I tune kNN by ten-fold cross-validation as in the notes, and then add one extra predictor that is pure noise. In linear regression this is fairly harmless: the new coefficient comes out near zero and the fit barely moves. In kNN the noise variable enters the Euclidean distance with the same weight as every useful variable, so the list of $k$ nearest neighbors itself changes. And since $\ell = (k/n)^{1/p}$, the neighborhood has to grow wider just to hold the same $k$ points.

So kNN gets punished for a variable that a linear model would quietly ignore. Does this mean we should always do some variable selection before fitting kNN, for instance keeping only the predictors with sizable lasso or ridge coefficients? If we do that, we are choosing variables with one model and then predicting with a different one, which feels a little inconsistent. And since kNN gives us no coefficients to inspect, how would we even notice that a useless variable is hurting us?
