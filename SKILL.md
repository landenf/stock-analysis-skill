---
name: stock-analysis
description: >
  Comprehensive financial analytics skill for evaluating individual stocks. Use this skill whenever
  a user asks to analyze, evaluate, research, or assess a stock or company — including requests like
  "analyze AAPL", "is META a good buy?", "give me a deep dive on NVDA", "what do you think of this
  stock?", "should I buy/sell X?", or "run a full analysis on [ticker]". Also trigger for any request
  involving fundamental analysis, technical analysis, valuation, earnings review, or investment thesis
  development for a specific equity. Even partial requests like "check the financials on X" or "how
  is X valued?" should activate this skill.
  
  MULTI-TICKER MODE: When the user passes in 2 or more tickers (e.g. "compare AAPL vs META" or
  "NVDA TSLA MSFT"), run the full analysis on EACH ticker, then produce a comparative table and
  two explicit verdicts: (1) Best Buy Today and (2) Best Long-Term Hold. Trigger this mode any time
  multiple tickers appear in the same request.
---

# Stock Financial Analytics Skill

A structured, multi-layer stock evaluation framework combining fundamental, technical, news/sentiment,
price target, and risk analysis into a consistent investment thesis. Designed for equity investors who
apply their own judgment — this skill structures the decision process, not the decision itself.

> ⚠️ Not financial advice. All analysis is for research and educational purposes only.

---

## Detecting Mode

**Single ticker** → Run all 8 layers → Output full thesis.

**Multiple tickers (2+)** → Run all 8 layers on EACH ticker → Output individual summaries →
Output comparative table → Output two verdict sections (Best Buy Today / Best Long-Term Hold).
See [Multi-Ticker Comparative Mode](#multi-ticker-comparative-mode) at the bottom of this skill.

---

## Step 1: Gather Inputs

If the user provides only a ticker (or tickers), proceed immediately using web search.
Otherwise note:
1. **Ticker(s)** — single or multiple
2. **Investment horizon** — swing (days/weeks), position (months), long-term (1+ year)
3. **Context** — any thesis or prior knowledge to incorporate?

---

## Step 2: Collect Data via Web Search

For each ticker, search for:
- Current price, 52-week range, ATH
- Income statement: revenue, gross profit, operating income, net income (TTM + last 3 FY)
- Balance sheet: cash, debt, equity
- Cash flow: operating CF, capex, FCF (TTM)
- Key ratios: P/E, EV/EBITDA, P/FCF, P/S, ROE, ROIC, gross margin, operating margin
- Analyst price targets: consensus, high, low, # of analysts, recent revisions
- Technical levels: current MAs (8, 21, 50, 100, 200), RSI, MACD
- Recent news: last 2–4 weeks of headlines
- Insider transactions: last 90 days
- Short interest: % of float, trend
- Next earnings date and consensus estimates

---

## Step 3: Run the Full Analysis Framework

Work through all 8 layers for each ticker.

---

### Layer 1: Business Quality

| Factor | What to Evaluate |
|--------|-----------------|
| **Revenue model** | Recurring vs. one-time? Hardware vs. software vs. services mix? |
| **Competitive moat** | Brand, switching costs, network effects, cost advantages, IP, regulatory licenses |
| **Market position** | Market share trend, TAM, growth runway |
| **Customer concentration** | Revenue concentration risk |
| **Insider ownership** | % held by insiders; recent buy/sell direction |
| **Management track record** | Capital allocation quality (buybacks, dividends, M&A), tenure |

**Output:** Moat rating (Wide / Narrow / None) + 2–3 sentence business quality summary.

---

### Layer 2: Fundamental Analysis

#### Growth Metrics
- Revenue growth: YoY and 3-year CAGR
- EPS growth: GAAP and non-GAAP trend
- FCF growth: accelerating or decelerating?
- Gross margin trend: expanding or compressing?

#### Profitability
- Gross margin, operating margin, net margin
- ROE — use with caution if book equity is negative (buyback-heavy companies)
- ROIC — NOPAT / Invested Capital; target >10%, ideally >WACC
- FCF margin — the cleanest profitability signal

#### Balance Sheet
- Net debt (debt minus cash) — net cash positive = strong
- Debt/Equity or Debt/EBITDA
- Interest coverage (EBIT / interest expense) — target >5x

#### Earnings Quality
- Accrual ratio: (Net Income - FCF) / Total Assets; near zero = high quality
- Watch for non-recurring items inflating headline earnings

**Output:** Fundamental scorecard (1–5) across growth, profitability, balance sheet, earnings quality.

---

### Layer 3: Valuation

#### Relative Multiples
| Multiple | Use Case |
|----------|---------|
| P/E (TTM + Forward) | Compare to sector median and own 3-year history |
| EV/EBITDA | Best cross-company comparison; removes capital structure |
| P/FCF | Cleanest cash-based multiple |
| P/S | Useful for pre-profit or high-growth names |
| PEG | P/E ÷ EPS growth rate; <1.0 suggests relative value |

#### Absolute Valuation
- **DCF range:** Model 3 scenarios (bear / base / bull FCF growth assumptions), WACC 8–12%
  - Output: implied fair value range (e.g. "$220–$290 base, $180 bear, $340 bull")
- **Reverse DCF:** At today's price, what growth rate is baked in? Is that achievable?

#### Price vs. Own History
- Current multiple vs. 3-year and 5-year average multiples
- Is it at a premium or discount to its own history?

**Output:** Valuation verdict (Undervalued / Fairly Valued / Overvalued) + implied upside/downside from base DCF.

---

### Layer 4: Price Target Analysis

Collect from web search:

| Item | What to Report |
|------|---------------|
| **Consensus PT** | Average analyst target across all rated analysts |
| **High PT** | Most bullish target and the firm behind it |
| **Low PT** | Most bearish target and the firm |
| **# of Analysts** | Buy / Hold / Sell rating distribution |
| **Upside to Consensus** | (Consensus PT − Current Price) / Current Price × 100 |
| **PT Revision Trend** | Have analysts raised or lowered targets in the last 90 days? Net upgrades vs. downgrades |
| **Implied Return** | Consensus PT upside + dividend yield = total implied 12-month return |

Note: analyst PTs are opinions, not guarantees. Report them as one data point among many.

**Output:** PT summary table + whether the consensus implies a risk/reward worth taking.

---

### Layer 5: Technical Analysis

Report all available MAs and indicators, organized clearly:

#### Moving Averages
| MA | Value | Price vs. MA | Signal |
|----|-------|-------------|--------|
| 8 EMA | $X | Above / Below | Bullish / Bearish |
| 21 EMA | $X | Above / Below | Bullish / Bearish |
| 50 SMA | $X | Above / Below | Bullish / Bearish |
| 100 SMA | $X | Above / Below | Bullish / Bearish |
| 200 SMA | $X | Above / Below | Bullish / Bearish |

Key interpretation rules:
- Price > 200 SMA = long-term uptrend intact (bullish market structure)
- Price > 50 SMA but < 200 SMA = intermediate trend recovery (watch)
- Price < 50 SMA and < 200 SMA = downtrend / avoid new longs
- 50 SMA crossing above 200 SMA = "Golden Cross" (bullish)
- 50 SMA crossing below 200 SMA = "Death Cross" (bearish)
- Price > 21 EMA and 21 EMA rising = momentum in force

#### Momentum & Oscillators
| Indicator | Value | Interpretation |
|-----------|-------|---------------|
| **RSI (14)** | X | <30 oversold, 30–50 bearish zone, 50–70 bullish zone, >70 overbought |
| **MACD** | Signal / Histogram | Bullish: MACD > Signal line and histogram expanding. Bearish: MACD < Signal |
| **Stochastic (14,3,3)** | X | <20 oversold, >80 overbought |

#### Volatility & Structure
| Metric | Value | Meaning |
|--------|-------|---------|
| **ATR (14)** | $X | Average daily range — use for stop sizing (e.g., stop = 2× ATR below entry) |
| **Bollinger Band Width** | X% | Narrow = volatility squeeze (breakout incoming); Wide = extended move |
| **52-week range position** | X% from low | (Current − 52wk Low) / (52wk High − 52wk Low) × 100 |
| **Distance from 200 SMA** | +X% | >20% above = extended, may mean-revert; <0% = underperformance |

#### Stage Classification (Weinstein)
- **Stage 1:** Basing — flat action above bottoming 200 SMA; wait for breakout
- **Stage 2:** Uptrend — price > rising 200 SMA; this is the buy zone
- **Stage 3:** Topping — price churning near highs; 200 SMA starting to flatten
- **Stage 4:** Downtrend — price below declining 200 SMA; avoid longs

#### Entry / Exit Framework
- **Buy zone:** Near key MA support, after base breakout on volume, or on Stage 2 pullback
- **Stop loss:** 2× ATR below entry, or below last swing low / key MA
- **Price target:** Analyst consensus PT or measured move from base
- **Risk/Reward:** Target ≥2:1

**Output:** Full MA table + indicators + Stage classification + Entry/Stop/Target if actionable.

---

### Layer 6: News & Sentiment

Search for the last 2–4 weeks of headlines. Report:

#### Recent Headlines (Top 5–8)
List each with date, source, and a one-line summary. Flag sentiment:
- 🟢 Bullish (earnings beat, product launch, upgrade, partnership, buyback announcement)
- 🔴 Bearish (miss, guidance cut, lawsuit, regulatory action, downgrade, executive departure)
- ⚪ Neutral (routine filing, conference appearance, analyst initiations at market weight)

#### Insider Activity (Last 90 Days)
| Type | # Transactions | Total $ Value | Signal |
|------|---------------|--------------|--------|
| Purchases | X | $X | Bullish if officers/directors buying |
| Sales | X | $X | Sales alone not necessarily bearish (planned 10b5-1) |

Red flag: large open-market insider sales without a pre-filed plan.

#### Short Interest
- Short % of float: X%
- Change vs. prior period: rising or falling?
- Interpretation: >10% float short = elevated bearish sentiment (but also short-squeeze fuel if thesis plays out)

#### Options Sentiment
- Put/Call ratio (if available): <0.7 = bullish sentiment, >1.2 = elevated fear/bearish positioning
- Notable unusual options activity (large block trades, elevated IV, etc.)

**Output:** News sentiment score (Bullish / Mixed / Bearish) + key headlines + insider/short summary.

---

### Layer 7: Macro & Sector Context

- **Sector trend:** Is the sector in favor? ETF flows, sector rotation signals
- **Interest rate sensitivity:** Rate-sensitive or not?
- **Economic cycle positioning:** Cyclical vs. defensive; early vs. late cycle
- **Institutional ownership:** 13F trend — accumulating or distributing?

**Output:** Macro tailwind / headwind score.

---

### Layer 8: Risk Assessment

| Risk Category | Examples |
|--------------|---------|
| **Business risk** | Competitive disruption, customer churn, product failure |
| **Regulatory/Legal** | Antitrust, fines, pending litigation |
| **Execution risk** | New market, acquisition, leadership change |
| **Valuation risk** | Multiple compression on miss |
| **Macro risk** | FX, rate sensitivity, geopolitical exposure |
| **Technical risk** | Below key MAs, breakdown from base |

**Output:** Risk rating (Low / Medium / High) + top 3 named risks.

---

## Step 4: Output — Single Ticker Thesis

```
TICKER: [Symbol] — [Company Name]
Date: [Today]
Price: $X | 52-wk Range: $X–$X | Market Cap: $X

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
BULL CASE
- [Reason 1]
- [Reason 2]
- [Reason 3]

BEAR CASE
- [Risk 1]
- [Risk 2]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FUNDAMENTALS
Revenue (TTM): $X | Growth: X% YoY
EPS (TTM): $X | Growth: X% YoY
FCF (TTM): $X | FCF Margin: X%
Gross Margin: X% | Op Margin: X% | Net Margin: X%
ROE: X% | ROIC: X%
Net Debt: $X (net cash positive / negative)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VALUATION
P/E (fwd): Xx | EV/EBITDA: Xx | P/FCF: Xx | PEG: X
DCF Fair Value: $X–$X (bear–bull range) | Base: $X
Upside to base DCF: X%
Verdict: Undervalued / Fairly Valued / Overvalued

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PRICE TARGETS
Consensus PT: $X | High: $X ([Firm]) | Low: $X ([Firm])
Buy / Hold / Sell: X / X / X analysts
Upside to consensus: X%
PT trend (90d): Mostly raised / Mostly lowered / Flat

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TECHNICAL SETUP
200 SMA: $X | 50 SMA: $X | 21 EMA: $X | 8 EMA: $X
RSI (14): X | MACD: Bullish / Bearish crossover
ATR (14): $X | BB Width: X% (Tight / Normal / Wide)
Stage: 1 / 2 / 3 / 4
Trend: Bullish / Neutral / Bearish
Entry zone: $X–$X | Stop: $X | Target: $X | R/R: X:1

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEWS & SENTIMENT (last 30 days)
🟢 [Headline] — [Date]
🔴 [Headline] — [Date]
⚪ [Headline] — [Date]
Insider: X purchases / X sales | Short float: X%
Overall sentiment: Bullish / Mixed / Bearish

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SCORECARD
Business quality:  X/5
Fundamentals:      X/5
Valuation:         X/5
Technical setup:   X/5
News & sentiment:  X/5
Overall conviction: X/5

THESIS
[3–4 sentences: what's the core thesis, what's the key risk, and what's the trigger to act]
```

---

## Multi-Ticker Comparative Mode

Triggered when 2 or more tickers are passed in.

### Step A: Run Full Analysis on Each Ticker
Complete all 8 layers for each. Output condensed single-ticker summaries (use the thesis block above for each).

### Step B: Comparative Table

After individual analyses, produce this table:

```
COMPARATIVE SNAPSHOT — [TICKER1] vs [TICKER2] (vs [TICKER3]...)
As of [Date] | Prices: TICKER1 $X | TICKER2 $X

METRIC                    TICKER1        TICKER2        BETTER
─────────────────────────────────────────────────────────────
Price                     $X             $X             —
Market Cap                $XB            $XB            —
Revenue (TTM)             $XB            $XB            —
Revenue Growth (YoY)      X%             X%             TICKER_
Gross Margin              X%             X%             TICKER_
Operating Margin          X%             X%             TICKER_
FCF Margin                X%             X%             TICKER_
EPS Growth (YoY)          X%             X%             TICKER_
ROE                       X%             X%             TICKER_
ROIC                      X%             X%             TICKER_
P/E (Forward)             Xx             Xx             TICKER_ (lower)
EV/EBITDA                 Xx             Xx             TICKER_ (lower)
P/FCF                     Xx             Xx             TICKER_ (lower)
PEG Ratio                 X              X              TICKER_ (lower)
DCF Upside (base)         X%             X%             TICKER_ (higher)
Consensus PT Upside       X%             X%             TICKER_ (higher)
200 SMA Position          +X%            +X%            TICKER_
RSI (14)                  X              X              —
Stage (Weinstein)         Stage X        Stage X        TICKER_
Short Float               X%             X%             TICKER_ (lower)
Moat Rating               Wide/Narrow    Wide/Narrow    TICKER_
Risk Rating               Low/Med/High   Low/Med/High   TICKER_
Scorecard Overall         X/5            X/5            TICKER_
```

### Step C: Verdict Section

After the table, always include this explicit section — do not skip:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🏆 BEST BUY TODAY: [TICKER]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[2–4 sentences explaining why this ticker wins on a near-to-medium term basis.
Consider: valuation relative to growth, technical setup/stage, PT upside, recent
news/catalysts, risk level. Be direct — don't hedge with "it depends."]

Primary reasons:
1. [Concrete reason — e.g., "Trading at 18x forward earnings vs. 32x for TICKER2, with faster
   EPS growth — the better risk/reward"]
2. [Technical reason — e.g., "Stage 2 uptrend with RSI at 54 vs. TICKER2's Stage 3 at RSI 71"]
3. [Catalyst reason — e.g., "Earnings beat + raised guidance last week; TICKER2 reports in 3 days
   with elevated implied move"]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🏆 BEST LONG-TERM HOLD (1–3 years): [TICKER]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[2–4 sentences. Note if this is the same as Best Buy Today and explain why, or explain
the divergence — e.g., near-term technicals favor X but long-term fundamentals favor Y.]

Primary reasons:
1. [Moat / business quality reason]
2. [Growth runway / TAM reason]
3. [FCF compounding / capital return reason]

Note: these can be the same ticker. If so, explain briefly why it wins both categories.
```

### Rules for the Verdict Section
- **Always give a definitive answer** — do not write "both are good choices" or "it depends on your risk tolerance" as the primary verdict. That is a cop-out. Make a call with stated reasoning.
- You may note caveats after the verdict, but the verdict itself must name a winner.
- If stocks are extremely close, pick the one with slightly better risk/reward and say so.
- Best Buy Today and Best Long-Term Hold may be the same or different tickers — assess independently.

---

## Reference Files

- `references/valuation-formulas.md` — DCF, WACC, ROIC, PEG, reverse DCF formulas
- `references/ratio-benchmarks.md` — Industry median ratios by sector
- `references/technical-indicators.md` — Detailed indicator definitions and interpretation rules

---

## Scope Notes

**This skill does:**
- 8-layer fundamental + technical + sentiment + price target analysis
- Single and multi-ticker comparative analysis with explicit verdicts
- Valuation modeling (multiples + DCF range)

**This skill does NOT:**
- Provide personalized investment advice
- Access live brokerage or real-time price feeds (uses web search)
- Execute trades or size positions
- Model options pricing

Always include the disclaimer: *For research and educational purposes only. Not financial advice.*
