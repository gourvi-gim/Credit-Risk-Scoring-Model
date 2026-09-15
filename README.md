# Credit Risk Scoring Model

Predicting corporate credit/default risk from financial statement ratios, 
using logistic regression on six standard ratios across 16 Indian companies.

## What this does
Screens companies for credit risk using Current Ratio, Debt-to-Equity, 
Interest Coverage, ROE, ROA, and Operating Profit Margin — the same 
fundamentals-first approach used in commercial credit analysis.

## Method
- Data: 16 companies across Real Estate, FMCG, Airlines, Infra, and Telecom 
  sectors (Yes Bank excluded — banks use CAR/NPA-based risk metrics, not 
  these ratios)
- Labels: rule-derived — a company is flagged High Risk if it trips 3+ of 
  6 threshold checks on the ratios above
- Model: Logistic Regression (scikit-learn), L2-regularized (C=0.1)

## Limitations (important — read before judging the numbers)
- **Labels are rule-derived from the same ratios used as features.** This 
  is a proof-of-concept for the ratio-analysis → scoring pipeline, not a 
  validated out-of-sample default predictor. A production version would 
  use actual defaults or credit rating bands (CRISIL/ICRA/CARE) as labels.
- **Small sample (n=16).** No train/test split or cross-validation was 
  performed — not meaningful at this sample size.
- **Some ratios are estimated, not individually verified** against source 
  filings (flagged in the workbook's Legend tab). Treat this as directionally 
  illustrative, not audit-grade data.

## Next steps
- Replace rule-based labels with real default/rating outcomes
- Expand sample size and verify all ratios against screener.in / company filings
- Add train/test evaluation once sample size allows it

## Files
- `GourviSharma_CreditRiskModel.xlsx` — full workbook (data, dashboard, model summary)
- `GourviSharmaCreditRisk.ipynb` — Python/scikit-learn model code
