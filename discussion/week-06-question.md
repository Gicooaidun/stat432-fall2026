---
id: w06-cgao19-imbalance-cutoff
title: "Should class imbalance change the cutoff?"
author: cgao19
---

The notes say that class imbalance alone does not change the Bayes cutoff of $1/2$. But in the logistic example only 29 percent of the cases are positive, and at cutoff $0.5$ the model catches only about 31 percent of them. Lowering the cutoff feels like the natural fix.

If imbalance is not a reason to move the cutoff, is lowering it really just a hidden way of saying that missing a positive costs more than a false alarm?
