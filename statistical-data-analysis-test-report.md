# Statistical Data Analysis v1.0 — Test Report & Product Listing

**File:** `index.html` (71.1 KB — limit 150 KB) · single file, all CSS/JS inline, zero external assets, zero network calls, no localStorage, no service workers, no permissions, no parent-window access. Safe for the sandboxed Wix iframe. The full statistics engine is written into the page — no libraries, no backend, no API keys. No requested feature requires a server.

## What it does
- **Data in:** upload CSV / TSV / TXT / JSON (≤ 5 MB), paste data, or a built-in 24-student sample dataset. Automatic delimiter detection (comma, semicolon, tab, pipe), quoted fields, thousands separators and European decimal commas handled; columns auto-typed numeric/categorical; missing values recognised (`NA`, `null`, `-`, empty…). Excel files: save as CSV first (explained on the page — a spreadsheet is a zipped package, and parsing it honestly needs a library larger than this app's budget).
- **Analyses:** Descriptive statistics (mean, median, mode, SD, variance, quartiles, IQR, skewness, kurtosis, 95% CI) · one-sample, independent (Welch or pooled) and paired t-tests with Cohen's d · one-way ANOVA with η² · chi-square test of independence with Cramér's V and a low-expected-count warning · Pearson & Spearman correlation matrices with significance · simple linear regression · multiple regression (standardised β, collinearity detection) · PCA (eigenvalues, variance %, loadings, scree plot) · factor analysis (principal axis factoring with iterated communalities + varimax rotation).
- **Out:** APA-style result tables, plain-language interpretation of every result, charts drawn on canvas (histogram, box plot, scatter with fitted line, scree), and a downloadable HTML report with the charts embedded.

## Product listing (for the Asif SaaS Studio CMS — `SaasProducts`)
- **Name:** Statistical Data Analysis — Tests, Regression, PCA & Factor Analysis
- **Slug:** `statistical-data-analysis`
- **Category:** Productivity
- **Version:** 1.0
- **Summary:** Analyse data in your browser: upload a CSV and run descriptives, t-tests, ANOVA, chi-square, correlation, regression, multiple regression, PCA and factor analysis — with tables, charts and plain-language interpretations. Your data never leaves your device.
- **appHtml:** upload `index.html` (this file)
- **Demo:** Yes · **Published:** Yes

## Verification — every number checked against scipy (the scientific reference)
- **41/41 statistical checks passed:** descriptives including adjusted skewness/kurtosis; t/F/chi-square/normal distribution functions; one-sample, pooled and Welch t-tests (statistic, df and p); paired t-test; ANOVA F and p; chi-square and p; Pearson and Spearman r and p; simple regression (slope, intercept, p, R²); multiple regression (all coefficients + R² vs numpy least squares); PCA eigenvalues vs numpy.
- **Factor analysis** recovered a planted two-factor structure exactly (variables clustered [F1,F1,F1,F2,F2,F2], all primary loadings > 0.6).
- **Parser & validation checks (13 + 7):** quoted CSV fields with embedded commas and escaped quotes; semicolon/tab sniffing; thousands separators → numbers; decimal commas → numbers; JSON in both object and row forms; missing-value handling; constant-column and perfect-collinearity rejections; too-few-cases rejection. A real bug was caught and fixed during testing: the t critical-value function initially bisected the wrong tail (95% CIs would have been 97.5% CIs) — now matches scipy to 3 decimals.
- Full inline scripts pass a JavaScript syntax check; file size verified at 71.1 KB.

## Manual testing checklist
- [ ] Open `index.html` in Chrome/Edge — loads cleanly, no console errors
- [ ] Load the sample dataset → preview shows 24 rows; StudyHours numeric, Group categorical
- [ ] Descriptive on PostTest → sensible mean/SD; histogram renders
- [ ] Independent t-test: PostTest by Gender (Welch) → table + box plot + interpretation
- [ ] ANOVA: PostTest by Group → F table; box plot shows Interactive highest
- [ ] Paired t-test: PreTest vs PostTest → large positive difference, significant
- [ ] Correlation matrix (all numeric) → StudyHours × PostTest strongly positive
- [ ] Regression: PostTest on StudyHours → fitted line on the scatter; equation shown
- [ ] Multiple regression: PostTest on StudyHours + PreTest → both predictors, R² shown
- [ ] PCA on the four numeric variables → variance table + scree plot
- [ ] Factor analysis, 2 factors → loadings table with communalities
- [ ] Upload your own CSV (and a JSON file) → loads; upload a 6 MB file → size error; paste garbage → clear error
- [ ] Download report → opens as a formatted page with tables and chart images
- [ ] Narrow the window to ~380 px → layout stacks, tables scroll horizontally
- [ ] After CMS upload, open `app.html?slug=statistical-data-analysis` on the live site → run the sample end-to-end inside the iframe
