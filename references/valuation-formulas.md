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

---

## FCF Yield & P/FCF

FCF Yield = Free Cash Flow / Market Cap  (the inverse of P/FCF)
- >5% = attractive cash return; >8% = cheap (assuming FCF is sustainable)
- P/FCF = Market Cap / FCF; <15x cheap, 15–25x fair, >30x expensive for a mature name
- Prefer FCF yield over earnings yield — cash is harder to manipulate than accounting earnings.

---

## Worked Examples

Numbers below are illustrative, not any real company.

### DCF — full walk-through
Assume: FCF (TTM) = $10.0B, shares = 1.0B, WACC = 9%, 5-yr FCF growth = 12%, terminal g = 3%.

1. **Project FCF for 5 years** (grow $10B at 12%):
   - Y1 11.20 · Y2 12.54 · Y3 14.05 · Y4 15.74 · Y5 17.62  ($B)
2. **Discount each** at 1/(1.09)^t:
   - 10.28 + 10.56 + 10.85 + 11.15 + 11.45 = **$54.29B** PV of explicit years
3. **Terminal value** at end of Y5 = FCF₅ × (1+g)/(WACC−g) = 17.62 × 1.03 / (0.09−0.03) = **$302.5B**
   - Discount to today: 302.5 / (1.09)^5 = **$196.6B**
4. **Enterprise value** = 54.29 + 196.6 = **$250.9B**
   - Add net cash (say +$20B) → equity value ≈ **$270.9B**
5. **Per share** = 270.9B / 1.0B = **~$271 base-case fair value**

Then rerun with bear (8% growth) and bull (16% growth) assumptions to get a range, e.g. "$210 bear / $271 base / $355 bull."

### Reverse DCF — what's priced in?
Stock trades at $271, WACC 9%, terminal g 3%, current FCF $10B, 1.0B shares. Solve for the 5-yr growth rate that makes the DCF output = $271. Here it's ~12%. Ask: *is 12% FCF growth realistic given history and TAM?* If the company has grown FCF 6%/yr, the market is pricing in an acceleration that may not happen → priced for perfection.

### PEG — worked
Forward P/E = 24x, consensus EPS growth = 20%. PEG = 24 / 20 = **1.2** → slightly expensive but reasonable for a quality grower. If growth were 30%, PEG = 0.8 → attractive.

### ROIC — decomposition
EBIT = $12B, tax rate = 21% → NOPAT = 12 × (1−0.21) = **$9.48B**.
Invested Capital = Equity $40B + Debt $15B − Cash $8B = **$47B**.
ROIC = 9.48 / 47 = **20.2%**. With WACC at 9%, the company earns ~11 pts above its cost of capital → strong value creation.

### EV bridge
Market Cap $250B + Total Debt $15B − Cash $8B + Minority Interest $1B + Preferred $0 = **EV $258B**.
Use EV (not market cap) in EV/EBITDA and EV/Revenue so leverage doesn't distort cross-company comparison.

---

## Sanity Checks
- **Terminal value should not dominate.** If >80% of DCF value comes from the terminal value, the model is really a bet on the perpetuity assumption — treat the output as low-confidence.
- **g must be < WACC**, and terminal g should not exceed long-run GDP (~2–3%). A terminal g near or above WACC produces an infinite/absurd value.
- **Cross-check multiples vs. DCF.** If DCF says "50% undervalued" but every multiple is at a sector premium, re-examine the growth assumptions — one of them is wrong.
- **Normalize cyclicals.** For cyclical businesses, base the DCF and multiples on mid-cycle FCF/EBITDA, not peak or trough.
