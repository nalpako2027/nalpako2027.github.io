---
title: "Accounting for Selection Bias for Causal Estimates"
categories:
  - Blog
tags:
  - Data Science
  - Causal Inference
  - A/B Testing
  - Business Analytics
  - propensity Score Matching
  - Quasi-experimental Data
---

Most businesses run A/B tests to measure impact between two groups. But those groups are frequently not the same. One group is self-selected, they don't represent the population of interest. The comparison is biased from the start! This is the "selection bias" problem — and it silently inflates ROI estimates (or produce less precise estimates), misleads strategy, and leads to poor resource allocation. So, how to solve the problem of being unable to randomly assign in your research or if it is too costly?

That's where Quasi-experimental methods becomes powerful.

Propensity Score Matching (PSM) is one of quasi-experimental methods that mimics a randomized experiment using observational data — matching treated and untreated groups on key theoretically relevant characteristics like age, income, or behavior patterns to eliminate selection bias.

In practice, this means you can answer questions like:
→ Did our loyalty program discount actually increase retention, or did it just attract/retain customers who would have stayed anyway?
→ Did the marketing campaign drive revenue, or did it reach customers already ready to buy?
→ What's the true ROI of an intervention when you can't (or didn't) run a randomized controlled trial? 
... using already existing observational data!

I recently applied PSM to a large educational PISA dataset and the results were striking — naive predictions significantly overestimated the treatment effect and underestimated its statistical error. PSM corrected for selection bias and gave a much more honest picture of impact.

PSM and other quasi-experimental methods (regression-discontinuity desing, difference-in-difference) are the most underused tools in the business analytics toolkit.
