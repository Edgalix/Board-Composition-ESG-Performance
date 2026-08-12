# Board Composition & ESG Performance: Technology vs Energy

An econometric comparison of how board characteristics (size, independence, gender
diversity, CEO duality) relate to ESG performance across the Technology and Energy
sectors, using a 5-year panel of 10 global firms (2019–2023).

## Question

How do board composition characteristics influence a firm's ESG score, and do these
relationships differ meaningfully between sectors with different risk profiles
(environmental-heavy Energy vs social/data-heavy Technology)?

## Method

- **Sample:** 10 firms × 5 years = 50 observations. Technology: Microsoft, NVIDIA,
  Apple, Alphabet, SAP. Energy: BP, Shell, TotalEnergies, ExxonMobil, Chevron.
- **Data source:** Bloomberg Terminal (ESG scores and board composition data). **Raw
  data is not included in this repository due to Bloomberg licensing restrictions** —
  see Data section below.
- **Model:** Pooled OLS — `ESG_Score ~ Board_Size + Pct_Independent_Directors +
  Pct_Women_on_Board + CEO_Duality + Industry_Dummy` — followed by separate
  sector-level OLS regressions for Technology and Energy.
- **Diagnostics:** Pearson correlation and VIF for multicollinearity; Breusch-Pagan for
  heteroskedasticity (with HC3 robust standard errors applied where detected);
  Durbin-Watson for autocorrelation.

## Headline result

- Board independence positively predicts ESG score in the pooled model (β=0.028,
  p=0.019) and strongly within Technology specifically (β=0.053, p=0.007).
- CEO duality significantly *reduces* ESG performance in Energy (β=-0.591, p<0.001) but
  has no significant effect in Technology — separating chair/CEO roles matters far more
  in high environmental-scrutiny sectors.
- Gender diversity is not significant in the pooled sample but is significant within
  Energy alone (β=0.023, p=0.013), suggesting sector context, not a universal effect,
  drives the relationship.

## Data availability

The Bloomberg-sourced panel dataset cannot be
redistributed here due to data licensing terms. The notebook documents the exact
variables, sample, and time period used so the analysis is fully reproducible by
anyone with their own Bloomberg Terminal access. A fully worked example run (with all
console output preserved) is included in the notebook for reviewers without terminal
access.

## Known limitations / next steps

- Small sample (n=50); results should be read as exploratory, not confirmatory.
- No firm fixed effects or lagged/control variables (financial performance, leverage)
  — a known simplification, discussed in the accompanying report.
- Low Durbin-Watson (0.577) indicates autocorrelation in the pooled panel, an expected
  limitation of pooled OLS on panel data without fixed effects.

## Run it

```bash
pip install -r requirements.txt
jupyter notebook Board_Composition_ESG.ipynb
```
