---
title: "Parameters vs. Statistics: A Terminology Gap Between Machine Learning and Classical Statistics"
categories:
  - Blog
tags:
  - Data Science
  - Machine Learning
  - Statistics
  - Terminology
header:
  teaser: "assets/images/statistics_parameters.png"
---

Have you ever stopped to ask why machine learning practitioners call it a 'parameter,' when, statistically speaking, it's almost always not one?

I've been studying XGBoost recently, and I realized that the term 'parameter' is used rather loosely among machine learning practitioners. In classical statistics, a parameter is a fixed, true value that describes a population, something we almost never actually observe. What we calculate from a sample--no matter how large it is--is an estimate, a statistic, our best guess at that unknown parameter. Indeed, the whole struggle of statistics and data science is to correctly generalize sample estimates to the population parameters. 
I wondered whether this understanding of 'parameter' was specific to the social sciences, so I looked it up in the Merriam-Webster dictionary: 

"[A] quantity (such as a mean or variance) that describes a statistical population" 

This definition corresponds to classical statistics definition. But in machine learning, "parameter" gets used to mean something a model learns a coefficient or a weight from its training data, which is really just sample data. By the classical definition, that's a sample-based estimate, not a population parameter at all.

I don't think this is a small semantic quirk. I guess Machine Learning's core vocabulary was largely built by computer scientists and engineers, often working on problems, signal processing, optimization, systems, where the population-versus-sample distinction was never central. And yet today, that same vocabulary gets applied constantly to deeply behavioral problems: predicting churn, modeling purchase behavior, recommending what someone watches next. Fields where sampling, measurement error, and the gap between a population and a sample are exactly what social scientists are trained to explore.
So when we say a model has "learned its parameters," we're borrowing a word from a discipline (of course, excluding math discipline here!) that would insist we call it a statistics, a statistical inference or a sample estimate. 

So next time someone says a model 'learned its parameters,' maybe the more honest phrase is: it estimated them.
