## Who Gets Left Out When We "Just Drop the Missing Cases"?

Every researcher who has stared down a messy dataset has felt the pull of the easy button: `regress y x1 x2 x3` and let Stata quietly discard every row with a blank cell. It's called listwise deletion, or complete-case analysis, and it feels harmless. The sample shrinks, the standard errors grow a little, and you move on.

But "shrinks a little" undersells what actually happens. In a recent analysis of early Algebra I placement and later mathematics achievement, running the model on complete cases alone cut the sample from over 19,000 students to just 6,368 — roughly a two-thirds reduction. That's not a minor footnote. It's the difference between a study and a shadow of one.

### The sensitivity check that told a bigger story

As a robustness check, the same regression that had been run on multiply imputed data was re-estimated using only students with no missing values on any model variable — this time with student weights and BRR weights with Fay adjustment applied. The coefficient pattern looked broadly similar across specifications, which is reassuring on its face. But look at the standard errors:

- Overall: β = 0.204, SE = 0.079
- Low tracked/disadvantaged background (TDB): β = 0.077, SE = 0.129
- Medium TDB: β = 0.254, SE = 0.128
- High TDB: β = 0.325, SE = 0.180

In the complete-case model, the TDB subgroup coefficients lost statistical significance. It would be tempting to read that as "the effect isn't really there." It's more accurate to read it as "we no longer have enough people to detect it." A sample cut by two-thirds doesn't just cost precision — it can quietly erase an effect that was real in the full data, simply by starving the model of power.

### But power loss was only half the problem

Here's the harder question, and the one that actually matters for interpretation: *who* was excluded? If missingness were purely random noise, the shrunken sample would still be a fair, if smaller, mirror of the population. It isn't. Listwise deletion doesn't discard cases evenly — it discards them systematically, according to whatever process generated the missing data in the first place.

Early Algebra I placement is not a neutral variable to study through this lens. A substantial line of research — Adelman (2006), Spielhagen (2006), and McEachin et al. (2020) among others — has established that early algebra functions as a gateway into advanced mathematics pathways, and that this gateway matters disproportionately for students from lower-SES backgrounds. If the students most likely to benefit from early acceleration are also the students most likely to be dropped from a complete-case sample, the analysis isn't just less precise — it's structurally biased against detecting the very effect it set out to measure.

So the study didn't stop at noticing the standard errors ballooned. It asked directly: are the excluded cases different in kind, not just in number?

### Letting the data answer the question

A post-hoc comparison flagged every complete case in the overall sample and compared its descriptive profile — using student weights — against every case that had been dropped due to missing data on at least one model variable.

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

The pattern is not subtle. The students who survived listwise deletion arrived with higher baseline achievement, higher SES, higher self-efficacy, higher expectations — their own and their parents' — and were less likely to be Black, Hispanic, English language learners, or enrolled in public schools. The students who got dropped were, almost across the board, the more disadvantaged half of the sample — precisely the group the early-algebra literature identifies as standing to gain the most from that early placement.

This is the mechanism by which complete-case analysis quietly biases a study: it doesn't announce itself as bias. It shows up as reduced significance, and it's easy to file that under "we just didn't have enough power." But when the missingness is entangled with the very demographic characteristics that predict the outcome of interest, what looks like a power problem is also a validity problem. The two are tangled together, and separating them requires exactly the kind of diagnostic comparison shown above.

### Why the imputed estimates deserve more trust here, not less

Multiple imputation doesn't fix this by magic. It works by exploiting auxiliary information — everything the dataset does know about a student, even when one particular variable is missing — to generate plausible values under the missing-at-random assumption, then propagates the uncertainty from that process into the standard errors (Rubin, 1987; Van Buuren, 2018). When the auxiliary variables are well chosen, the resulting estimates draw on the full sample's demographic and academic diversity rather than only the subset lucky enough to have complete records.

That's not a minor technical preference. Francis Huang and Brian Keller, writing about missing data in large-scale educational assessments, note that despite decades of research documenting listwise deletion as a suboptimal strategy that produces biased estimates, it remains the de facto default in applied education research — often because software defaults to it silently, and because reviewers rarely ask for anything else. Their broader point echoes what the diagnostic comparison above shows directly: when the "de facto default" is left unexamined, findings about the very populations most affected by educational interventions can be understated or missed entirely.

Deborah Newman's methodological guidance points in the same direction from a different angle: missing data can produce two distinct problems — biased parameter estimates, and inaccurate hypothesis tests or standard errors — and social scientists continue to reach for listwise and pairwise deletion, the more error-prone techniques, more often than the evidence would justify. That's a useful reminder that "the coefficients look similar" is not the same as "the model is unbiased." Coefficients can survive a bad missing-data strategy while still understating precisely the effect a study was designed to find.

### The takeaway

Complete-case analysis isn't wrong because it's lazy. It's wrong because it makes an invisible assumption — that missingness is unrelated to the outcome you care about — and that assumption rarely survives contact with real educational data. Students who are missing achievement scores, SES information, or self-efficacy ratings are not a random subset of the population. They tend to be the students already facing the steepest odds, which means the analysis that drops them tends to understate the very disparities it set out to describe.

The fix isn't complicated in principle: flag your complete cases, compare them to your incomplete cases on every variable that matters, and let that comparison tell you whether your missingness is a nuisance or a warning sign. In this case, it was clearly the latter — and multiple imputation, not listwise deletion, produced the estimates that actually represent the population the study intended to describe.

---

**References**

Adelman, C. (2006). *The toolbox revisited: Paths to degree completion from high school through college*. U.S. Department of Education.

Huang, F., & Keller, B. (2025). Working with missing data in large-scale assessments. *Large-scale Assessments in Education, 13*(13). https://doi.org/10.1186/s40536-025-00248-9

McEachin, A., Domina, T., & Penner, A. (2020). Understanding the effects of accelerated middle school algebra. *Journal of Research on Educational Effectiveness, 13*(1), 71–99.

Newman, D. A. (2014). Missing data: Five practical guidelines. *Organizational Research Methods, 17*(4), 372–411. https://doi.org/10.1177/1094428114548590

Rubin, D. B. (1987). *Multiple imputation for nonresponse in surveys*. Wiley.

Spielhagen, F. R. (2006). Closing the achievement gap in math: The long-term effects of eighth-grade algebra. *Journal of Advanced Academics, 18*(1), 34–59.

Van Buuren, S. (2018). *Flexible imputation of missing data* (2nd ed.). CRC Press.
