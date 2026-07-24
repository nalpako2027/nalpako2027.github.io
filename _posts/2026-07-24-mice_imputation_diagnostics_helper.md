---
title: "A Diagnostics Package for Multiple Imputation by Chained Equations (using PMM)"
layout: single
show_excerpts: false
categories:
  - Repository
tags:
  - Data Science
  - Multiple Imputation
  - Predictive Mean Matching
  - Missing Data
  - Python
link: "https://github.com/nalpako2027/mice_imputation_diagnostics_helper.git"
header:
  teaser: "assets/images/mice_process.png"
---

🚀 Excited to share a project I've been working on:

A Diagnostics Package for Multiple Imputation by Chained Equations (MICE) using Predictive Mean Matching (PMM)

📊 Missing data is an unavoidable challenge in survey and administrative datasets, and the way we handle it can substantially influence every downstream analysis and decisions based on analysis its results. 

I started building this package while conducting a fixed-effects model analysis on TIMSS 2023 longitudinal data. During that project, I found that existing open-source implementations fell short in ways that mattered for both research and industry applications—for example, undocumented matching behavior, limited diagnostic capabilities, and a lack of support for survey design weights.

This package implements MICE with Predictive Mean Matching (PMM), with the implementation designed to be auditable against the foundational work of Rubin (1987) and van Buuren's Flexible Imputation of Missing Data.

✨ Key features include:

• 📐 Rubin's Rules pooling diagnostics (FMI, RVI, and Relative Efficiency)

• 🧮 Von Hippel's recommended number of imputations (M)

• 📈 Convergence trace plots

• 📋 Population statistics before and after imputation

• ⚖️ Optional support for weighted analyses in complex survey data

The goal was to create a transparent and auditable implementation for research and industry applications where understanding and validating the imputation process is just as important as obtaining the completed dataset.

💻 GitHub repository:

https://lnkd.in/enEsxGkB


I hope it proves useful for researchers, data scientists, and analysts working with missing data. Feedback and suggestions are always welcome!

#DataScience #Statistics #MissingData #Imputation #MICE #PMM #Python
