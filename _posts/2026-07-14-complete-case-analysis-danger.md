---
title: "The Danger of "Just Dropping the Missing Cases"
categories:
  - Blog
tags:
  - Data Science
  - Missing Data
  - Listwise Deletion
  - Multiple Imputation
  - Mathematics Achievement
  - Teacher Deficit Beliefs
---

## The Danger of "Just Dropping the Missing Cases" 🔍 

Majority of researchers/data analysts in social sciences or relevant private sectors pull the easy button during analysis: let their statistical software (e.g., Stata or SPSS) quietly discard every row with a blank cell with respect to the variables of interest. It's called listwise deletion, or complete-case analysis. The sample shrinks, and they move on, feeling that that is a harmless move. And sometime it is! Some even go so far as to delete incomplete cases 'from the data' without any theoretical justification, or cherry-pick data to find 'significant results'. I will not discuss this, as it is tantamount to manipulating the data. This not only invalidates any results obtained, but is also completely unethical!

Anyway, "shrinking the sample a little" undersells what actually happens. Recently, I conducted an analysis using High School Longitudinal Study (HSLS); running the regression model on complete cases alone cut the sample from over 19,000 students to just 6,368 — roughly a two-thirds reduction. That's not a minor footnote. It's the difference between a study and a shadow of one.

Moreover, my study was about whether mathematics teachers' deficit beliefs (TDB) and Early Algebra Enrollment influence students' long-term mathematics achievement. The huge reduction in the sample size raised the question of who is more likely to leave equity-related items unanswered.

### ⚠️ The Sensitivity Check That Told a Bigger Story

I imputed the data using Multiple Imputation by Chained Equations (MICE) and run the analysis on imputed data. As a robustness check, I ran the same regression model on complete cases. The coefficient pattern looked roughly similar across specifications, which is reassuring on its face. 
However, in the complete-case model, the TDB subgroup coefficients lost statistical significance due to larger standard errors. It would be tempting to read that as "the effect isn't really there." It's more accurate to read it as "we no longer have enough people to detect it." A sample cut by two-thirds doesn't just cost precision — it can quietly erase an effect that was real in the full data, simply by starving the model of power.

### 📉 But Power Loss Was Only Half the Problem...

Here's the harder question, and the one that actually matters for interpretation: *who* was excluded during list-wise deletion? If missingness were purely random noise, the shrunken sample would still be a fair, if smaller, mirror of the population. It isn't. Listwise deletion doesn't always discard cases evenly — it may discard them systematically, according to whatever process generated the missing data in the first place.

The study's variables of interest (TDB and Early Algebra I placement) are not a neutral variables to study through this lens. A substantial line of research — Adelman (2006), Spielhagen (2006), and McEachin et al. (2020) among others — has established that early algebra functions as a gateway into advanced mathematics pathways, and that this gateway matters disproportionately for students from lower-SES backgrounds. If the students most likely to benefit from early acceleration or negatively affected by TDB are also the students most likely to be dropped from a complete-case sample, the analysis isn't just less precise — it's structurally biased against detecting the very effect it set out to measure.

So the study didn't stop at noticing the standard errors ballooned. It asked directly: are the excluded cases different in kind, not just in number?

### 📊 Letting the Data Answer the Question

For the post-hoc comparison, I flagged every complete case in the overall sample and compared its descriptive profile (using student weight, BRR weights etc.) against every case that had been dropped due to missing data on at least one model variable.

| Variable | Complete cases (N=6,368) | Incomplete cases (N=12,866) |
|---|---|---|
| Baseline math achievement | 0.869 | 0.494 |
| Early Algebra I placement | 0.297 | 0.214 |
| Highest 8th-grade math grade | 4.138 | 3.891 |
| Math self-efficacy | 3.017 | 2.889 |
| Student expectation | 6.953 | 6.455 |
| SES | 0.103 | −0.107 |
| Parent expectation | 3.229 | 3.137 |
| Conceptual teaching | 3.302 | 3.248 |
| Public school | 0.905 | 0.934 |
| Black or Hispanic | 0.269 | 0.376 |
| English language learner | 0.014 | 0.030 |

The students who survived listwise deletion arrived with higher baseline achievement, higher SES, higher self-efficacy, higher expectations — their own and their parents' — and were less likely to be Black, Hispanic, English language learners, or enrolled in public schools. The students who got dropped were, almost across the board, the more disadvantaged — precisely the group the Early-Algebra literature identifies as standing to gain the most from that early placement (and likely to be negatively affected by TDB).

This is the mechanism by which complete-case analysis quietly biases a study: it doesn't announce itself as bias. It shows up as reduced significance, and it's easy to file that under "we just didn't have enough power." But when the missingness is entangled with the very demographic characteristics that predict the outcome of interest, what looks like a power problem is also a validity problem. The two are tangled together, and separating them requires exactly the kind of diagnostic comparison shown above.

### ✅ Why The Imputed Estimates Deserve More Trust, Not Less

Multiple imputation doesn't fix this by magic. It works by exploiting auxiliary information — everything the dataset does know about a student, even when one particular variable is missing — to generate plausible values under the missing-at-random assumption, then propagates the uncertainty from that process into the standard errors (Rubin, 1987; Van Buuren, 2018). When the auxiliary variables are well chosen, the resulting estimates draw on the full sample's demographic and academic diversity rather than only the subset lucky enough to have complete records.

That's not a minor technical preference. Francis Huang and Brian Keller, writing about missing data in large-scale educational assessments, note that despite decades of research documenting listwise deletion as a suboptimal strategy that produces biased estimates, it remains the de facto default in applied education research — often because software defaults to it silently, and because reviewers rarely ask for anything else. More importantly, many researchers apply statistical procedures without understanding the underlying assumptions and mechanisms that govern them. Treating statistical analysis as a black box — running a procedure without knowing what it assumes about the data-generating process — is methodologically problematic.

Newman's (2014) methodological guidance points in the same direction from a different angle: missing data can produce two distinct problems — biased parameter estimates and inaccurate standard errors or hypothesis tests — yet social scientists continue to reach for listwise and pairwise deletion, the more error-prone techniques, more often than the evidence would justify. This distinction is important for more than just statistical accuracy: 'The coefficients look similar' does not mean 'the model is unbiased', and a biased, underpowered estimate can be — and has been — misread or misused as evidence that inequalities are smaller than they actually are. This undermines the very equity arguments. 

### 🎯 The Takeaway

Complete-case analysis isn't wrong because it's lazy. It's wrong because it makes an invisible assumption — that missingness is unrelated to the outcome you care about — and that assumption rarely survives contact with real educational data. Students who are missing achievement scores, SES information, or self-efficacy ratings are not a random subset of the population. They tend to be the students already facing the steepest odds, which means the analysis that drops them tends to understate the very disparities it set out to describe.

The fix isn't complicated in principle: flag your complete cases, compare them to your incomplete cases on every variable that matters, and let that comparison tell you whether your missingness is a nuisance or a warning sign. In this case, it was clearly the latter — and multiple imputation, not listwise deletion, produced the estimates that actually represent the population the study intended to describe.  


Although this analysis originates from educational research, its implications can be applied directly to any data science setting outside of academia. Businesses routinely build models based on incomplete records, such as customer surveys with skipped fields, transaction logs with dropped sessions and sensor data with outages. Defaulting to listwise deletion in this context carries the same hidden risk: the customers, transactions or regions with missing data are rarely random, and excluding them can systematically underestimate churn risk, misprice segments or hide the very disparities that fairness or credit-scoring models are designed to detect. Failing to impute data is not just a loss of sample size and statistical power; it is a decision, often made unnoticed, to allow the model's representation of 'the customer' or 'the population' to be disproportionately influenced by those who filled out the survey. Therefore, in the private sector, viewing imputation as a significant modelling choice rather than an optional step is one of the most effective ways to prevent the deployment of a flawed model.


---

**References**

Adelman, C. (2006). *The toolbox revisited: Paths to degree completion from high school through college*. U.S. Department of Education.

Huang, F., & Keller, B. (2025). Working with missing data in large-scale assessments. *Large-scale Assessments in Education, 13*(13). https://doi.org/10.1186/s40536-025-00248-9

McEachin, A., Domina, T., & Penner, A. (2020). Understanding the effects of accelerated middle school algebra. *Journal of Research on Educational Effectiveness, 13*(1), 71–99.

Newman, D. A. (2014). Missing data: Five practical guidelines. *Organizational Research Methods, 17*(4), 372–411. https://doi.org/10.1177/1094428114548590

Rubin, D. B. (1987). *Multiple imputation for nonresponse in surveys*. Wiley.

Spielhagen, F. R. (2006). Closing the achievement gap in math: The long-term effects of eighth-grade algebra. *Journal of Advanced Academics, 18*(1), 34–59.

Van Buuren, S. (2018). *Flexible imputation of missing data* (2nd ed.). CRC Press.
