# Monthly Wage Analysis and Prediction in R

Academic project by **Claudio Raffaele Salerno** — academic year **2025/2026**.

Analysis of monthly wages and their association with individual, educational, employment and geographical characteristics using the WAGE2 dataset and generalized linear models in R. The original report is written in Italian.

**[Read the report (PDF)](Analisi-e-Previsione-salario-mensile.pdf)** · **[View the R Markdown source](Analisi%20e%20Previsione%20salario%20mensile.Rmd)**

## Methods

- Exploratory analysis: descriptive statistics, contingency tables, correlations, boxplots, density plots and Q-Q plots.
- Gaussian regression of log wages.
- Gamma regression with log and inverse links, and inverse Gaussian regression with a log link.
- Model comparisons using likelihood-ratio tests, AIC and BIC.
- A 75/25 training/test split with random seed `125`.
- Predictive evaluation using MAE and RMSE, predictions for illustrative profiles and adjusted prediction plots.

## Results

The report selects a reduced Gamma model with a log link, excluding `age`, among the positive-response specifications compared. The predictive errors reported for the Gamma and Gaussian log-wage models are close:

| Model | Test MAE | Test RMSE |
| --- | ---: | ---: |
| Gamma with log link | 245.73 | 329.54 |
| Gaussian on log wages, with exponentiated predictions | 243.23 | 331.10 |

## Data

`wage2.xls` is the original Excel dataset supplied with this project and is included alongside the analysis.

WAGE2 contains monthly earnings and information on hours worked, IQ, knowledge of the world of work, education, experience, tenure, age, marital status, race, geographical location and family background. The [wooldridge documentation](https://justinmshea.github.io/wooldridge/reference/wage2.html) attributes the data to Blackburn and Neumark (1992), using observations for 1980.

## Run locally

1. Extract all files into one project directory and open it in RStudio.
2. Install the required packages:

```r
install.packages(c(
  "readxl", "car", "tidyverse", "fitdistrplus", "ggeffects", "recipes",
  "tidymodels", "caret", "corrplot", "ggplot2", "cowplot", "see",
  "knitr", "rmarkdown"
))
```

3. The source contains the author's original absolute Windows path. Set the spreadsheet path in your local working copy to its location on your computer; when working from the extracted directory, use:

```r
wag <- readxl::read_excel("wage2.xls")
```

4. Open the R Markdown file and knit it. The source supports PDF, HTML and Word output. PDF rendering requires LaTeX.

The supplied PDF can be read directly without running R.

## Files

- `Analisi e Previsione salario mensile.Rmd` — original analysis source.
- `Analisi-e-Previsione-salario-mensile.pdf` — original report.
- `wage2.xls` — WAGE2 data in Excel format.
- `README.md` — project overview, data source and execution instructions.
- `.gitignore` — exclusions for local R session and rendering files.

The original R Markdown, PDF and Excel dataset are preserved unchanged.
