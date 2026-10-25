---
id: w09-cgao19-radial-svm-c-gamma
title: "Can a smaller C compensate for a larger gamma?"
author: cgao19
---

In the radial SVM, increasing $\gamma$ makes similarity decay faster with distance, while decreasing $C$ gives more weight to the coefficient penalty. Both seem to affect how flexible the fitted boundary is, but they change different parts of the model.

If $\gamma$ is so large that each observation is similar only to points very close to it, can making $C$ smaller still recover a smooth boundary that captures the broader class pattern? Or does it mainly weaken a fit whose similarities are already too local? How would this differ from keeping $C$ fixed and reducing $\gamma$ instead?
