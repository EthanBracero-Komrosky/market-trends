
# Can Treasury Yield Movements Help Anticipate Short-Term Equity Market Behavior?

## Project Summary

This project explored the relationship between changes in the 10-Year U.S. Treasury yield and short-term S&P 500 market performance using historical financial data from FRED (Federal Reserve Economic Data).

The main goal of the analysis was to look at whether movements in Treasury yields contain predictive information about next-day equity market direction and whether such information could hold value within broader institutional investment strategies.

---

# Motivation

Interest rates are one of the most important macroeconomic variables in financial markets. Changes in Treasury yields can influence:

- borrowing costs,
- equity valuations,
- investor risk appetite,
- and broader economic expectations.

Institutional investors and hedge funds frequently monitor Treasury markets to help guide portfolio positioning and risk management decisions.

This project investigated whether daily changes in Treasury yields are associated with short-term stock market behavior and whether those changes may provide incremental predictive value.

---

# Data Sources

The analysis used historical daily market data downloaded from FRED:

## Datasets
- **SP500** — S&P 500 Index
- **DGS10** — 10-Year Treasury Constant Maturity Yield

## Time Range
- May 9, 2016 → May 7, 2026

This range included multiple distinct macroeconomic regimes:
- low-interest-rate environments,
- the COVID-19 crash,
- post-pandemic recovery,
- inflationary periods,
- and aggressive Federal Reserve tightening cycles.

---

# Data Cleaning and Preprocessing

The raw datasets were cleaned and merged using Python and pandas.

Key preprocessing steps included:

- converting date columns into datetime objects,
- converting numerical values from strings into numeric data types,
- handling missing values,
- and merging both datasets by trading date.

Rows containing missing observations were removed to ensure consistent analysis across both variables.

---

# Feature Engineering

Several new variables were created from the raw financial data:

## 1. Daily S&P 500 Returns

Daily market returns were calculated using percentage change:

\[
\frac{P_t - P_{t-1}}{P_{t-1}}
\]

This transformed raw index values into measures of short-term market performance.

---

## 2. Daily Treasury Yield Changes

Daily Treasury yield changes were calculated using first differences:

\[
Y_t - Y_{t-1}
\]

This captured shifts in the interest-rate environment rather than absolute yield levels.

---

## 3. Binary Prediction Target

A classification target was created to determine whether the S&P 500 closed positive or negative on the following trading day.

Target variable:
- `1` = market positive next day
- `0` = market negative next day

This allowed the project to frame the problem as a binary classification task.

---

# Exploratory Data Analysis

Time-series visualizations were created for:
- the S&P 500,
- and the 10-Year Treasury yield.

The graphs revealed several important macroeconomic trends:

## Treasury Yield Trends
- historically low yields during the COVID period,
- significant yield increases beginning in 2021–2022,
- increased volatility during inflation and Federal Reserve tightening cycles.

## Equity Market Trends
- sharp market decline during COVID,
- strong recovery following 2020,
- elevated volatility during rising-rate environments.

---

# Relationship Between Yield Changes and Market Returns

A scatterplot comparing:
- daily Treasury yield changes,
- and daily S&P 500 returns

revealed a highly noisy relationship with no strong linear structure.

## Correlation Analysis

The calculated correlation between:
- `Yield_Change`
- and `SP500_Return`

was:

\[
0.1255
\]

This indicated a weak positive relationship during the selected time period.

Interestingly, this result differed from the commonly assumed belief that rising interest rates necessarily harm equities.

One possible explanation is that portions of the dataset captured periods where rising yields reflected:
- economic recovery,
- stronger growth expectations,
- and improving corporate earnings sentiment.

This highlighted an important financial insight:

> the market impact of rising yields depends heavily on broader macroeconomic context and investor interpretation.

---

# Predictive Modeling

A logistic regression classification model was developed to test whether Treasury yield changes could help predict next-day market direction.

## Model Inputs
Feature:
- `Yield_Change`

Target:
- `Next_Day_Positive`

## Machine Learning Workflow
- 80/20 train-test split
- logistic regression classifier
- prediction accuracy evaluated on unseen test data

---

# Model Results

The model achieved:

\[
53.7\%
\]

prediction accuracy on next-day market direction.

---

# Interpretation of Results

Although predictive power was modest, the results were still meaningful in a financial context.

Financial markets are highly noisy systems influenced by:
- macroeconomic conditions,
- earnings,
- monetary policy,
- geopolitics,
- investor psychology,
- and many additional variables.

As a result, single-variable prediction models rarely achieve extremely high accuracy.

However, even small statistical edges may still hold value when:
- applied at institutional scale,
- incorporated into larger quantitative systems,
- or combined with additional market signals.

The project demonstrated that Treasury yield movements may contain incremental informational value relevant to:
- portfolio positioning,
- macroeconomic regime analysis,
- and risk management frameworks.

---

# Business Implications

Institutional investors and hedge funds could potentially use Treasury yield signals to support:

- volatility forecasting,
- macroeconomic monitoring,
- dynamic hedging strategies,
- sector rotation models,
- or broader quantitative investment systems.

For firms managing large portfolios, even modest improvements in forecasting or risk management may translate into:
- reduced drawdowns,
- improved risk-adjusted returns,
- and preservation of significant capital.

While the signal identified in this project would likely be insufficient as a standalone trading strategy, it may contribute value when integrated into more sophisticated multi-factor investment frameworks.

---

# Limitations

Several limitations should be acknowledged:

- only one predictive feature was used,
- markets are influenced by many interacting variables,
- relationships between rates and equities may change across market regimes,
- and logistic regression captures only relatively simple relationships.

Additionally, correlation does not imply causation.

---

# Future Improvements

Potential future enhancements include:
- incorporating inflation and unemployment data,
- adding Federal Reserve policy variables,
- testing volatility indices such as the VIX,
- using lagged variables and rolling windows,
- exploring nonlinear machine learning models,
- and analyzing sector-specific market responses.

---

# Conclusion

This project investigated whether movements in the 10-Year Treasury yield contain predictive information about short-term equity market behavior.

The analysis found:
- a weak positive correlation between yield changes and market returns,
- and modest predictive performance (~53.7% accuracy) when forecasting next-day market direction.

Although the predictive signal was limited, the project demonstrated how macroeconomic variables may still contribute useful information within broader financial modeling and investment frameworks.

More broadly, the project highlighted the complexity of financial markets and the challenges associated with extracting reliable predictive signals from noisy economic data.
