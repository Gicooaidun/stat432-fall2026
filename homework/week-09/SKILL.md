---
name: stat432-svm
description: Compare SVM classifiers and produce a one-page analysis report. Load only when explicitly invoked with a dataset, response, predictors, coding, and output directory.
---
# SVM analysis

Invoke only on explicit request. Ask for missing data details; do not infer variable names.
Keep the analysis and report reproducible; use seed 43209 unless the invocation overrides it.

1. Audit sample size, class counts, missingness, types, constants, duplicates, and dependence.
   Judge whether numeric distances and the available class sizes support SVM classification.
   Explain categorical coding; impute or remove constants inside fitting folds if needed.
   Use a grouped or temporal split for dependent data; stop if a defensible split is impossible.
2. Reserve a stratified 30% test set before tuning; use five stratified training folds.
   Reuse identical folds for every candidate. Fit all preprocessing on fitting rows only.
   Reduce the fold count if class sizes require it and explain the change.
3. Explain kernel choices: linear as a baseline, low-degree polynomials for interactions,
   and radial for local nonlinear patterns. Use no more than 20 predeclared settings.
   Default grid: C in {0.1, 1, 10} for linear and polynomial degrees {2, 3, 4};
   radial C in {0.1, 1, 10} crossed with gamma in {0.01, 0.1}: 18 settings total.
   For polynomials fix gamma=1/p and coef0=1, with p the encoded predictor count.
   Standardize predictors; use unweighted classes, tolerance 1e-7, and no probability fitting.
   Any grid adaptation must precede candidate results; state all fixed settings.
4. Default to equal-cost misclassification. For binary classes sorted as (a,b),
   predict b when its oriented decision score is at least zero; otherwise predict a.
   For multiple classes use the library vote rule and report its tie handling.
   State any requested costs or weights before tuning. Scores are not probabilities.
5. Record all fold errors, their arithmetic mean, and sample SD/sqrt(number of folds).
   Call this SE descriptive: overlapping fitting folds prevent an independent-fold CI.
   Let T=min mean CV error + the SE of that minimum-error candidate.
   Among settings with mean error <= T, choose lexicographically by kernel order
   linear, polynomial degree 2, degree 3, degree 4, radial; then smaller C,
   then smaller gamma, then lower CV error. Resolve exact ties by the listed grid order.
   This is an explicit simplicity convention, not a universal complexity ranking.
6. Freeze the selection, refit its pipeline on all training rows, then score the test set once.
   Report only this model's test error, Wilson 95% interval, confusion matrix, sensitivity,
   specificity, and support-vector count. Do not revise choices using test results.
7. Save analysis-report.pdf and its source in the supplied output directory.
   Use one printed page, 11-point text, and margins of at least 1.5 cm.
   Include setup, kernel rationale, grid, folds, selection rule, and the selected settings.
   Include one compact figure of all CV errors and T; mark the selected and minimum rows.
   Include one table of each kernel's best CV candidate plus the selected row if different.
   Give CV mean and SE, selected test results, a training majority baseline, and limitations.
   Interpret differences cautiously; avoid causal claims or unsupported superiority claims.
8. Check counts, folds, leakage, selection, arithmetic, convergence, and all report requirements.
   Keep the code and full CV table. Render and visually inspect the PDF; shorten prose
   or reduce the figure before changing font size. Never silently omit required evidence.
