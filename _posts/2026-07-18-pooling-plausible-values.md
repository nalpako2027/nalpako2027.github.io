---
title: "TIMSS-style pooling of Plausible Values (Rubin's Rules + JRR)"
layout: single
show_excerpts: false
categories:
  - Repository
tags:
  - machine learning
  - logistic regression
  - knn
  - business insights
link: "<script src="https://gist.github.com/nalpako2027/70883718f74081b78ade06cbb6b3e18f.js"></script>"

---

This Python function implements TIMSS's official pooling methodology for wide-format Plausible Values, following the TIMSS Technical Report rather than a generic multiple-imputation approach. It calculates the pooled mean and its standard error using survey sampling weights (Rubin's Rules for imputation variance) and replicate weights (Jackknife Repeated Replication for sampling variance). See the TIMSS documentation for the underlying formulas: 2023 Ch.13 | 2019 Ch.14
