# Statistical Data Analysis — Tests, Regression, PCA & Factor Analysis

A complete statistics workbench in a single web page — **100% in your browser**. No uploads, no sign-up, no server: your data never leaves your device.

**▶ Live on Asif SaaS Studio:** open the tools catalogue and choose *Statistical Data Analysis* (slug `statistical-data-analysis`).

## What it does
1. **Load data** — CSV, TSV, TXT or JSON upload, paste, or the built-in 24-student sample dataset. Delimiters are auto-detected; quoted fields, thousands separators, decimal commas and missing-value tokens are handled.
2. **Analyse** — descriptive statistics; t-tests (one-sample, independent Welch/pooled, paired) with Cohen's d; one-way ANOVA (η²); chi-square (Cramér's V); Pearson/Spearman correlations; simple and multiple regression (standardised β, collinearity detection); PCA (Jacobi eigensolver); factor analysis (principal axis factoring + varimax).
3. **Read** — a standard statistical table, a chart, and a plain-language interpretation under every result.
4. **Report** — download a formatted HTML report with tables and chart images.

Excel files are not parsed (honestly signposted in the app): save as CSV first.

## Use
Open `index.html` in any modern browser — or from this repo via any static host. No build step, no dependencies.

- Single file, **71.1 KB**, all CSS/JavaScript inline
- No localStorage, no service workers, no browser permissions, no parent-window access — safe in a sandboxed iframe
- Responsive layout in the Asif SaaS Studio emerald + lime branding

## Testing
**41/41 numeric checks against scipy** (the scientific reference implementation): descriptives including adjusted skew/kurtosis, all t-test variants including Welch degrees of freedom, ANOVA, chi-square, correlations, OLS vs a least-squares reference, PCA eigenvalues — plus a factor-analysis test that recovered a planted two-factor structure exactly, and 20 parser/validation checks. Full report: `statistical-data-analysis-test-report.md`. Complete documentation: `docs/statistical-data-analysis-docs.pdf`.

Created by Dr. Asif Ahmad · Asif SaaS Studio · v1.0
