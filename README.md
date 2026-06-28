# Stock Portfolio Risk & Return Dashboard

A Python-based analysis of risk and return across a 10-stock equity portfolio (NSE-listed), comparing three allocation strategies and presenting results in an Excel dashboard.

## Overview

This project evaluates 5 years of historical price data (2019–2024) for 10 NSE-listed stocks across multiple sectors, calculates standard risk/return metrics, and compares three different portfolio allocation strategies (Aggressive, Moderate, Conservative) on a risk-adjusted basis.

## Stocks analysed

RELIANCE, TCS, HDFCBANK, INFY, ITC, WIPRO, SBIN, MARUTI, SUNPHARMA, HINDUNILVR (all `.NS`)

## Methodology

1. **Data collection** — pulled 5 years of adjusted closing prices via the `yfinance` API
2. **Return calculation** — computed daily returns, then annualised metrics per stock:
   - CAGR (Compound Annual Growth Rate)
   - Annualised volatility (standard deviation × √252)
   - Sharpe Ratio (risk-adjusted return)
   - Maximum Drawdown
3. **Correlation analysis** — built a correlation matrix to evaluate diversification benefit across holdings
4. **Portfolio construction** — modelled three allocation strategies with different sector weightings:
   - Aggressive
   - Moderate
   - Conservative
5. **Dashboard** — exported all outputs to a multi-sheet Excel workbook with an embedded visual dashboard

## Key results

| Metric | Insight |
|---|---|
| Highest CAGR | Identified via per-stock comparison (see notebook) |
| Lowest volatility | Identified via per-stock comparison (see notebook) |
| Best Sharpe Ratio (portfolio level) | Compared across the 3 allocation strategies |
| Diversification | Correlation matrix shows low/moderate correlation across sectors, supporting risk reduction through diversification |

*(Run the notebook to regenerate exact figures — they will update if you change the date range or universe.)*

## Tech stack

- Python 3
- `yfinance` — price data
- `pandas`, `numpy` — data manipulation and metric calculations
- `matplotlib`, `seaborn` — visualisation
- `openpyxl` — Excel export

## Repository contents

| File | Description |
|---|---|
| `portfolio_analysis.ipynb` | Full Jupyter notebook — data pull, metric calculations, visualisations |
| `portfolio_dashboard.xlsx` | Final Excel deliverable with 5 sheets (Price Data, Daily Returns, Stock Metrics, Portfolio Summary, Dashboard) |
| `portfolio_dashboard.png` | Exported static image of the 4-panel dashboard chart |

## How to run

```bash
pip install pandas numpy yfinance matplotlib seaborn openpyxl jupyter
jupyter notebook portfolio_analysis.ipynb
```

Run all cells in order. The notebook will pull live data from Yahoo Finance, so results will reflect the latest available prices rather than a frozen snapshot.

## Dashboard preview

![Portfolio Dashboard](portfolio_dashboard.png)

## Notes & limitations

- Three allocation strategies were manually specified rather than derived via optimisation (e.g. mean-variance / Efficient Frontier) — a natural next step would be to add an optimiser.
- Sharpe Ratio calculations use a simplified risk-free rate assumption; refine with the actual contemporaneous T-bill/G-Sec rate for more precision.
- Past performance shown here is historical and does not indicate future results.
