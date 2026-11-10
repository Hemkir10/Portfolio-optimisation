# Portfolio Optimisation using Markowitz Mean-Variance Model

**Course:** IM21204 – Operations Research II  
**Project:** Portfolio Optimisation

## Overview

This project applies the **Markowitz Mean-Variance Portfolio Optimisation** framework to allocate capital across a basket of nine equity stocks and one gold exchange-traded fund (ETF). The model finds portfolio weights that meet specified target returns of **10%** and **15%** while minimising portfolio variance (risk).

## Objectives

- Analyse historical return and risk characteristics of selected assets.
- Construct a portfolio using multiple equities and a gold ETF.
- Estimate relationships between assets using correlation and covariance.
- Determine the minimum-risk allocation for target returns of 10% and 15%.
- Compare the resulting portfolio risk and illustrate the effect of compounding over time.

## Assets considered

The project report lists the following nine companies:

1. Titan
2. Tata Steel
3. State Bank of India (SBIN)
4. NTPC
5. Coal India
6. JSW Steel
7. Axis Bank
8. Reliance
9. Hindalco

**Gold instrument:** Tata Gold ETF.

The report states that the companies were selected based on their average rate of return and standard deviation. Tata Gold ETF was chosen instead of physical gold because its exchange-traded daily price series can be analysed alongside stock prices using the same return, variance and covariance calculations.

## Methodology and workflow

### 1. Collect historical price data

Historical price observations for the selected companies and Tata Gold ETF were assembled in the project dataset. The dataset is linked below. A consistent daily price series is needed so that returns for the different assets can be compared over the same observation periods.

### 2. Calculate asset returns and risk

For each asset, the project analyses daily and annualised returns and standard deviations. Returns represent changes in price over time; standard deviation is used as a measure of the variability (risk) of those returns.

The report refers to a separate spreadsheet tab named **“N21 Analysis”** for the detailed company-level analysis. The PDF does not state the exact observation date range or the annualisation convention used, so those implementation details should be checked in the spreadsheet/notebook before reproducing the results.

### 3. Measure relationships between assets

Portfolio risk depends not only on the individual volatility of each asset but also on how asset returns move in relation to one another.

The project presents a **correlation matrix** and a **covariance matrix**. The results pages state that the covariance matrix (Σ) was constructed using manually entered standard deviations and historical correlations.

### 4. Define the optimisation model

Let:

- \(w_i\) be the proportion of total capital invested in asset \(i\);
- \(\mu_i\) be the expected return of asset \(i\);
- \(\Sigma\) be the covariance matrix of asset returns;
- \(R_T\) be the target portfolio return.

The portfolio variance is minimised:

\[
\min_{\mathbf{w}}\quad \mathbf{w}^{T}\Sigma\mathbf{w}
\]

Subject to the full-investment constraint:

\[
\sum_{i=1}^{n}w_i=1
\]

and the target-return constraint:

\[
\mathbf{w}^{T}\boldsymbol{\mu}=R_T
\]

The project report also specifies non-negative portfolio weights:

\[
w_i\geq 0
\]

Thus, the portfolio is fully invested, meets the specified target return, and does not use negative asset weights (short positions).

### 5. Solve for the target returns

The optimisation was implemented in Python using the Google Colab notebook linked below. The model was run separately for target returns of **10%** and **15%**. For each run, it reports the optimal asset weights, portfolio expected return and portfolio standard deviation.

### 6. Compare the allocations and risk

The optimal allocations shown in the report are:

| Asset | Weight at 10% target | Weight at 15% target |
|---|---:|---:|
| Titan | 0.00% | 2.62% |
| Tata Steel | 0.00% | 0.00% |
| SBIN | 0.00% | 7.81% |
| NTPC | 19.63% | 20.29% |
| Coal India | 0.00% | 0.00% |
| JSW Steel | 10.81% | 8.87% |
| Axis Bank | 19.15% | 17.81% |
| Reliance | 50.41% | 42.59% |
| Hindalco | 0.00% | 0.00% |
| Tata Gold ETF | 0.00% | 0.00% |
| **Total** | **100.00%** | **100.00%** |

The report's optimisation output gives:

| Target expected return | Portfolio standard deviation |
|---:|---:|
| 10.00% | 15.41% |
| 15.00% | 14.43% |

These figures are transcribed from the submitted report. They are model outputs based on the inputs used in the project, not guarantees of future investment performance.

### 7. Visualise portfolio growth

The report includes a portfolio growth chart comparing hypothetical growth at 10% and 15% annual returns over a 20-year period. It illustrates how different annual growth rates can lead to substantially different outcomes through compounding. This chart is an illustration of growth at assumed rates, not a forecast.

## Project files and links

- **Dataset / analysis spreadsheet:** [Google Sheets – N21 Analysis](https://docs.google.com/spreadsheets/d/13HvlP40jfuld_xE-nuh9ebEf04haEz3fq-prXkW65Os/edit?usp=sharing)
- **Python implementation:** [Google Colab notebook](https://colab.research.google.com/drive/1vSfhgFTkg8HXOtlW7qRfHOvHmdExUbQA)

If you publish this repository, check that the spreadsheet and notebook sharing permissions are appropriate. Do not upload credentials, private tokens, or personal information.

## Tools and concepts

- Python (Google Colab)
- Historical financial data analysis
- Expected return and standard deviation
- Correlation and covariance matrices
- Markowitz Mean-Variance Optimisation
- Constrained portfolio allocation
- Portfolio growth visualisation

## Limitations and reproducibility notes

The submitted PDF does not specify the exact historical data period, detailed data-cleaning steps, precise return formula/annualisation factor, or the optimisation library/solver settings. These should be documented from the spreadsheet and notebook if the project is to be independently reproduced. The reported allocations and risk values should be interpreted in the context of the data and assumptions used at the time of the analysis.

## Disclaimer

This repository documents an academic Operations Research project. It is for educational purposes only and is not investment advice or a recommendation to buy or sell any security.
