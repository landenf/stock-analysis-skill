# Valuation Formulas Reference

## DCF (Discounted Cash Flow)

### Basic Formula
Intrinsic Value = Σ [FCFt / (1 + WACC)^t] + Terminal Value / (1 + WACC)^n

### Terminal Value
Terminal Value = FCFn × (1 + g) / (WACC - g)
- g = long-term growth rate (typically 2–3%, no higher than GDP growth)
- WACC = weighted average cost of capital

### WACC Estimate by Risk Profile
| Profile | WACC Range |
|---------|------------|
| Large-cap, stable, low-debt | 7–9% |
| Mid-cap, moderate growth | 9–11% |
| High-growth, unprofitable | 11–15% |
| Small-cap, speculative | 15%+ |

### Reverse DCF
Given current stock price, back into implied FCF growth rate:
Price × shares = PV of all future FCF
Solve for g. If implied g is unrealistic (>30% for 10 years), the stock is priced for perfection.

---

## ROIC

ROIC = NOPAT / Invested Capital
- NOPAT = EBIT × (1 - tax rate)
- Invested Capital = Total Equity + Total Debt - Cash

Rule of thumb: ROIC > WACC = value creation; ROIC < WACC = value destruction.

---

## PEG Ratio

PEG = (P/E) / (5-year EPS growth rate)
- PEG < 1.0 → potentially undervalued relative to growth
- PEG > 2.0 → expensive relative to growth
- Best used for consistent growers; unreliable for cyclicals or pre-profit companies

---

## EV / EBITDA

Enterprise Value = Market Cap + Total Debt - Cash + Minority Interest + Preferred
EBITDA = Operating Income + Depreciation + Amortization

EV/EBITDA removes capital structure differences — better for comparing companies across industries.

---

## Accrual Ratio (Earnings Quality)

Accrual Ratio = (Net Income - FCF) / Average Total Assets
- Near zero = high earnings quality (cash matches profit)
- Highly positive = company books profits it hasn't collected in cash (red flag)
- Highly negative = company collects more cash than reported profit (green flag)
