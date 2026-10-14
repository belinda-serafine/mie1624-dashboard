# Developer Pay Review: Remote Work and Education

An interactive, client-facing dashboard that presents a statistical analysis of the **2025 Stack Overflow Developer Survey**. It looks at two questions:

1. Do **remote** developers earn more than **hybrid** developers?
2. In the **US and Canada**, does salary differ by **education level** (Bachelor's, Master's, Professional degree)?

**Live dashboard:** https://YOUR-USERNAME.github.io/mie1624-dashboard/

## Key findings

| Question | Result |
|---|---|
| Remote vs hybrid, mean salary | Remote earns **$12,071 more** ($113,861 vs $101,790); t = 2.5819, p = 0.0098 |
| 95% CI for the gap | $2,907 to $21,235 (formula); $2,482 to $20,532 (bootstrap) |
| Remote vs hybrid, median salary | $90,526 vs $77,730; Mood's median test p ≈ 1.27 × 10⁻²⁵ |
| Education (US & Canada) | Bachelor's $160,988 · Master's $182,221 · Professional $197,701; ANOVA F = 17.50, p = 2.70 × 10⁻⁸ |

## What's in the dashboard

- **Executive summary** of the key takeaways, written for a non-technical audience
- **Exploratory analysis:** job satisfaction by job title, mean salary by job title, and annual salary vs age
- **Remote vs hybrid:**
  - descriptive statistics and the outlier decision
  - manual, SciPy and Welch two-sample t-tests
  - bootstrapped distributions (10,000 replications)
  - t-test on the bootstrapped data
  - formula-based and bootstrap 95% confidence intervals
  - Mood's median test compared with bootstrapped medians
- **Education level:** descriptive statistics, one-way ANOVA, bootstrapped and pairwise difference distributions, and ANOVA on the bootstrapped data
- **Further views:**
  - salary and satisfaction across all four work arrangements
  - salary percentile profile
  - a country-by-country check of the remote premium
- A plain-language **glossary** of the statistical terms

Each result comes with a "What this means for you" explanation.

## Methods

- **Data:** cleaned Stack Overflow Developer Survey 2025 (20,407 respondents with reported annual salary in USD)
- **Outliers:** one extreme salary ($33,552,715) was removed before the hypothesis tests
- **Tests:** two-sample t-test (pooled and Welch), bootstrap resampling (10,000 replications, `np.random.seed(22)`), Mood's median test, and one-way ANOVA, at α = 0.05
- **Tools:** Python (pandas, NumPy, SciPy, Matplotlib) for the analysis, HTML/CSS with Chart.js for the dashboard

## Data privacy

The dashboard embeds **only aggregated results** (summary statistics, histogram bin counts and test results). No individual survey responses are published. The age vs salary view uses binned counts instead of individual points.

## Running locally

The dashboard is a single self-contained `index.html` file. You can open it in any modern browser. An internet connection is needed to load Chart.js and the web fonts.

## Credits

- Analysis and dashboard by **Belinda Serafine**, MEng (Mechanical & Industrial Engineering), University of Toronto. Prepared for MIE1624: Introduction to Data Science, Analytics and AI (Fall 2026).
- The dashboard was built with the help of Claude (Anthropic).
- Survey data: [Stack Overflow Developer Survey](https://survey.stackoverflow.co).
