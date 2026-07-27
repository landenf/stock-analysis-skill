# Technical Indicators Reference

## Cheat Sheet — Thresholds at a Glance

| Indicator | Bearish | Neutral | Bullish |
|-----------|---------|---------|---------|
| **Price vs. 200 SMA** | Below, 200 falling | Around it, flat | Above, 200 rising |
| **Price vs. 50 SMA** | Below | At/near | Above and rising |
| **50 vs. 200 SMA** | Death Cross (50<200) | — | Golden Cross (50>200) |
| **RSI (14)** | <40 and falling | 40–50 | 50–70 (healthy) |
| **RSI extreme** | >80 with bearish divergence | — | <30 in an uptrend (reversal) |
| **MACD** | MACD < Signal, below zero | Flat, near zero | MACD > Signal, histogram expanding |
| **Stochastic (14,3,3)** | >80 rolling over | 20–80 | <20 turning up |
| **Bollinger** | Riding lower band in downtrend | Squeeze (direction TBD) | Breakout above upper band |
| **Volume** | Up on down days (distribution) | Below average | Rising on up days / breakouts |
| **Weinstein Stage** | Stage 4 | Stage 1 or 3 | Stage 2 |
| **RS vs. S&P 500** | RS line rolling over | Sideways | RS at/near new highs |

> Read indicators as a **weight of evidence**, not a single trigger. One bullish reading in a Stage 4 downtrend is noise; five aligned readings in Stage 2 is a setup.

---

## Moving Averages

### Simple Moving Average (SMA)
Average closing price over N periods. Each period weighted equally.
- **50 SMA**: Intermediate trend. Widely watched by institutions. A break below is often the first warning sign.
- **100 SMA**: Medium-term trend. Acts as support/resistance in trending markets.
- **200 SMA**: The definitive long-term trend line. Price above = bull market structure; below = bear.
  - "Distance from 200 SMA" = (Price − 200 SMA) / 200 SMA × 100
  - >20% above = historically extended; mean reversion risk rises
  - <−20% below = deeply oversold; watch for capitulation/reversal setups

### Exponential Moving Average (EMA)
Weights recent prices more heavily. Reacts faster to price changes than SMA.
- **8 EMA**: Very short-term momentum. Used by traders for entries/exits in active trends.
- **21 EMA**: The key swing-trade moving average. In a healthy uptrend, pullbacks find support here.
  - Rule: In a Stage 2 uptrend, a stock bouncing off the rising 21 EMA on lower volume is a low-risk add.
  - Red flag: Price closing below 21 EMA on heavy volume = momentum shift, reduce or exit.

### Golden Cross & Death Cross
- **Golden Cross**: 50 SMA crosses above 200 SMA → long-term bullish signal (lagging, but reliable)
- **Death Cross**: 50 SMA crosses below 200 SMA → long-term bearish signal

### Key MA Rule of Thumb (from simplest to most actionable)
1. Price > 200 SMA → trend is up, bias long
2. Price > 50 SMA and 50 SMA > 200 SMA → strong uptrend, add on pullbacks to 21 EMA
3. Price < 50 SMA but > 200 SMA → consolidation/pullback, wait for reclaim
4. Price < 200 SMA → avoid new longs; only trade if confirming reversal with volume

---

## Momentum Indicators

### RSI — Relative Strength Index (14 periods)
Measures the speed and magnitude of price movements on a 0–100 scale.

| RSI Level | Interpretation |
|-----------|---------------|
| < 30 | Oversold — potential reversal zone (buy signal in uptrending stocks) |
| 30–50 | Bearish zone — momentum is weak |
| 50 | Neutral pivot — above = bullish bias, below = bearish bias |
| 50–70 | Bullish zone — momentum is healthy |
| > 70 | Overbought — not a sell signal alone; strong stocks stay overbought |
| > 80 | Historically extended; watch for divergence (price new high, RSI lower high = weakness) |

**RSI Divergence:**
- Bearish: Price makes a new high, RSI makes a lower high → hidden weakness
- Bullish: Price makes a new low, RSI makes a higher low → hidden strength

**RSI in context:** In strong bull markets, RSI can stay between 50–80 for months. Don't short a stock just because RSI is 70. Look for *divergence*, not just absolute levels.

---

### MACD — Moving Average Convergence Divergence
Default settings: 12 EMA − 26 EMA = MACD Line; 9 EMA of MACD = Signal Line; Histogram = MACD − Signal.

| Signal | Interpretation |
|--------|---------------|
| MACD crosses above Signal | Bullish crossover — buy signal |
| MACD crosses below Signal | Bearish crossover — sell/caution signal |
| Histogram expanding positively | Momentum accelerating upward |
| Histogram shrinking (positive) | Momentum decelerating — watch for reversal |
| MACD below zero and falling | Strong downtrend |
| MACD above zero and rising | Strong uptrend |

**Divergence:** Same concept as RSI — price new high + MACD lower high = bearish divergence.

---

### Stochastic Oscillator (14, 3, 3)
Compares closing price to the high-low range over 14 periods. %K and %D lines on 0–100 scale.

| Level | Interpretation |
|-------|---------------|
| < 20 | Oversold |
| > 80 | Overbought |
| %K crosses above %D below 20 | Bullish signal |
| %K crosses below %D above 80 | Bearish signal |

Best used in ranging/consolidating markets. Less reliable in strong trends.

---

## Volatility Indicators

### ATR — Average True Range (14 periods)
Measures average daily price range. Not directional — only measures volatility magnitude.

**Primary uses:**
1. **Stop sizing:** Place stop 1.5× or 2× ATR below entry. Avoids getting stopped out by normal noise.
   - Example: Stock at $100, ATR = $3. Stop at $94 (2× ATR) = $6 risk per share.
2. **Position sizing:** Risk per trade ÷ (2× ATR) = shares to buy.
3. **Volatility screening:** Compare ATR to historical ATR to detect volatility squeezes.

Low ATR relative to history = volatility compression → breakout setup brewing.

---

### Bollinger Bands (20 SMA ± 2 standard deviations)
Envelope around price showing relative volatility.

| Signal | Interpretation |
|--------|---------------|
| **Bollinger Band Squeeze** (bands narrow) | Volatility compression; major move incoming — direction unknown |
| Price touches upper band | Overbought in range-bound market; in uptrend = continuation |
| Price touches lower band | Oversold in range-bound; in downtrend = continuation |
| **Bandwidth expanding** | Breakout in progress — trend is establishing |

**Band Width Formula:** (Upper Band − Lower Band) / Middle Band × 100
- <5% = very tight squeeze (rare; precedes large moves)
- 10–20% = normal
- >30% = extended volatility

---

## Volume Analysis

Volume confirms or contradicts price action. Never trade off price alone.

| Pattern | Meaning |
|---------|---------|
| Price up + Volume above 20-day avg | Strong demand — bullish confirmation |
| Price up + Volume below avg | Weak breakout — suspect; may fail |
| Price down + Volume above avg | Heavy selling — distribution, bearish |
| Price down + Volume below avg | Normal pullback — not alarming |
| Volume spike on reversal bar | Potential climax (capitulation or blow-off top) |

**Volume Dry-Up (VDU):** Price pullbacks on very low volume within an uptrend = normal digestion, not distribution. Often the best low-risk entry point.

---

## Weinstein Stage Analysis

Stan Weinstein's market stage model classifies where a stock is in its price cycle.

| Stage | Price vs. 200 SMA | 200 SMA Direction | Volume Pattern | Action |
|-------|------------------|------------------|---------------|--------|
| **1 — Base** | Near / just above | Flattening | Declining | Wait — accumulation happening |
| **2 — Uptrend** | Above and rising | Rising | Rising on breakout | BUY — this is the sweet spot |
| **3 — Top** | Still above but choppier | Flattening / rolling | High & erratic | Reduce / Exit |
| **4 — Downtrend** | Below | Declining | High on breaks | NO new longs |

**Stage 2 entry signal:** Price breaks above Stage 1 base on volume ≥1.5× average, 200 SMA has flattened or is beginning to rise, RS line vs. S&P 500 breaking to new high.

**Stage 4 warning signals:** Price below 200 SMA for 3+ weeks, 200 SMA has rolled over and is declining, rallies fail at declining 200 SMA.

---

## Relative Strength vs. S&P 500

RS Line = Stock Price / SPX Price (plotted over time)
- RS making new highs while stock consolidates = bullish accumulation
- RS breaking down before price = early warning of underperformance
- RS line rising faster than price = institutional accumulation

Strong stocks have RS lines that lead price to new highs before the stock makes new highs.
Weak stocks have RS lines that roll over before the stock breaks down.

---

## Quick Reference — Indicator Combinations

### Strong Buy Setup
- Price > 21 EMA > 50 SMA > 200 SMA (all rising)
- RSI between 50–70 (healthy momentum, not extended)
- MACD above signal line, histogram expanding
- Volume: breakout on 1.5–2× average, pullbacks on dry volume
- Bollinger Bands: just emerging from squeeze
- Stage 2
- RS line at or near new highs

### Caution / Wait Setup
- Price between 50 SMA and 200 SMA (in no-man's land)
- RSI between 40–50 (weak momentum)
- MACD below signal or flat
- Stage 1 or transitioning from Stage 3

### Avoid / Short Setup
- Price < 200 SMA, 200 SMA declining
- RSI < 40 and trending lower
- MACD below zero and declining
- Volume rising on down days
- Stage 4
