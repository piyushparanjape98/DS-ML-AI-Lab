# Statistics

This folder covers the core statistical concepts and hypothesis tests used for data analysis and inference — descriptive statistics, probability theory, and the major hypothesis tests (Z, T, Chi-Square, ANOVA), plus correlation analysis.

## Contents

### 01_Descriptive_Statistics
**What it covers:** Mean, median, mode, variance, standard deviation, range, percentiles, skewness, kurtosis.

**Key formulas:**
- Mean: $\bar{x} = \frac{\sum x_i}{n}$
- Variance: $\sigma^2 = \frac{\sum (x_i - \bar{x})^2}{n}$
- Standard Deviation: $\sigma = \sqrt{\sigma^2}$

**Application:** Summarizing a dataset's central tendency and spread before any modeling — the first step in any EDA.

**Advantage:** Fast, simple, gives an immediate feel for the data's shape and outliers.

**Disadvantage:** Only describes the sample at hand — doesn't tell you anything about the broader population or whether patterns are statistically meaningful.

---

### 02_Probability
**What it covers:** Probability rules, distributions (normal, binomial, Poisson, etc.), conditional probability, Bayes' theorem.

**Key formulas:**
- Conditional Probability: $P(A|B) = \frac{P(A \cap B)}{P(B)}$
- Bayes' Theorem: $P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$
- Normal Distribution PDF: $f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$

**Application:** Foundation for every hypothesis test and ML model that relies on likelihood — e.g. Naive Bayes, confidence intervals, p-values all trace back to this.

**Advantage:** Provides the mathematical basis to quantify uncertainty rather than just describing data.

**Disadvantage:** Assumes an underlying distribution — real-world data often doesn't fit cleanly (skewed, multimodal), which breaks the assumptions of downstream tests.

---

### 03_Z_test
**What it covers:** Hypothesis testing for comparing means when population variance is known and sample size is large (n > 30).

**Key formula:**
$$Z = \frac{\bar{x} - \mu}{\sigma / \sqrt{n}}$$

where $\bar{x}$ = sample mean, $\mu$ = population mean, $\sigma$ = population standard deviation, $n$ = sample size.

**Application:** Comparing a sample mean to a known population mean (e.g. "is our website's average load time different from the industry standard of 2s?").

**Advantage:** Simple, well-understood, works well with large samples.

**Disadvantage:** Requires knowing the population standard deviation, which is rarely known in practice — and unreliable for small samples.

---

### 04_T_test
**What it covers:** One-sample, two-sample (independent), and paired T-tests for comparing means when population variance is unknown.

**Key formulas:**
- One-sample: $t = \frac{\bar{x} - \mu}{s / \sqrt{n}}$
- Two-sample (independent): $t = \frac{\bar{x}_1 - \bar{x}_2}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}$

where $s$ = sample standard deviation (used since population $\sigma$ is unknown).

**Application:** Comparing means between two groups with small sample sizes — e.g. "did a new drug improve recovery time compared to a control group?"

**Advantage:** Doesn't require population variance to be known, works well even with small samples (n < 30).

**Disadvantage:** Assumes the underlying data is approximately normally distributed; sensitive to outliers, especially in small samples.

---

### 05_Chi_Square_test
**What it covers:** Chi-Square goodness-of-fit test and test of independence for categorical data.

**Key formula:**
$$\chi^2 = \sum \frac{(O_i - E_i)^2}{E_i}$$

where $O_i$ = observed frequency, $E_i$ = expected frequency.

**Application:** Checking if two categorical variables are related (e.g. "is customer churn related to subscription plan type?"), or if observed frequencies match an expected distribution.

**Advantage:** Works directly with categorical/count data — no normality assumption needed on the raw variable.

**Disadvantage:** Sensitive to sample size — very large samples can flag trivial associations as "significant"; unreliable with small expected cell counts (<5).

---

### 06_ANOVA_test
**What it covers:** Analysis of Variance — comparing means across three or more groups (one-way, two-way ANOVA).

**Key formula:**
$$F = \frac{\text{Between-group variance}}{\text{Within-group variance}} = \frac{MSB}{MSW}$$

where $MSB = \frac{SSB}{k-1}$, $MSW = \frac{SSW}{n-k}$, $k$ = number of groups, $n$ = total sample size.

**Application:** Testing whether multiple groups differ significantly — e.g. "does average sales differ across four store regions?" Avoids running multiple T-tests, which inflates false-positive risk.

**Advantage:** Efficiently compares many groups at once in a single test, controlling for the multiple-comparisons problem.

**Disadvantage:** Only tells you *that* a difference exists somewhere, not *which* groups differ — needs a post-hoc test (e.g. Tukey's HSD) to pinpoint that. Also assumes normality and equal variance across groups (homoscedasticity).

---

### 07_Correlation.ipynb
**What it covers:** Pearson and Spearman correlation coefficients, correlation matrices/heatmaps.

**Key formula (Pearson):**
$$r = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum (x_i - \bar{x})^2 \sum (y_i - \bar{y})^2}}$$

**Application:** Measuring the strength and direction of relationships between numeric variables — often a first pass before feature selection in ML.

**Advantage:** Quick, interpretable, and a single number (-1 to 1) summarizes the relationship.

**Disadvantage:** Pearson correlation only captures *linear* relationships — can completely miss strong non-linear ones; correlation never implies causation.
