---

id: w03-cgao19-ridge-step-size
title: "Choosing lambda for prediction versus optimization"
author: cgao19
------------------

In ridge regression, increasing \(\lambda\) increases the smallest eigenvalues of the objective's curvature matrix and can improve the condition number, which may make gradient descent converge faster. However, a larger \(\lambda\) also introduces more shrinkage bias.

If a larger value of \(\lambda\) makes the optimization problem easier, why should we still choose \(\lambda\) based on prediction criteria such as cross-validation rather than computational properties such as the condition number or convergence speed? Is there ever a situation where optimization efficiency should influence the choice of \(\lambda\), or should these two considerations always be treated separately?
