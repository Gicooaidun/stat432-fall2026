---
id: w07-cgao19-lda-qda-small-samples
title: "If QDA is more flexible, why can LDA work better?"
author: cgao19
---

LDA assumes that all classes share one covariance matrix, while QDA estimates a separate covariance matrix for each class. Suppose the classes really do have different covariance matrices, but there are only a few training observations in each class. QDA seems to match the true situation better.

Why could LDA still make fewer mistakes on new observations, even though its shared-covariance assumption is wrong? How would we expect this comparison to change as we collect more training data while keeping the number of predictors fixed?
