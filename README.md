# Stock Analysis Skill

A [Claude](https://claude.com/claude-code) skill that turns any ticker (or set of tickers) into a
structured, multi-layer equity analysis — fundamentals, valuation, technicals, price targets,
news/sentiment, and risk — assembled into a consistent investment thesis.

> ⚠️ **Not financial advice.** All output is for research and educational purposes only.

## What it does

Ask Claude something like:

- `analyze AAPL`
- `is META a good buy?`
- `give me a deep dive on NVDA`
- `compare AMD vs NVDA vs INTC`

…and the skill runs an 8-layer framework on each ticker:

1. **Business Quality** — moat, market position, insider ownership, management
2. **Fundamentals** — growth, profitability, balance sheet, earnings quality
3. **Valuation** — relative multiples, DCF range, reverse DCF, price-vs-own-history
4. **Price Targets** — consensus/high/low, analyst distribution, revision trend
5. **Technicals** — moving averages, RSI/MACD/Stochastic, ATR/Bollinger, Weinstein stage, entry/stop/target
6. **News & Sentiment** — recent headlines, insider activity, short interest, options positioning
7. **Macro & Sector** — sector trend, rate sensitivity, cycle positioning, institutional flow
8. **Risk** — business, regulatory, execution, valuation, macro, and technical risk

### Single vs. multi-ticker

- **One ticker** → full 8-layer analysis + a single-ticker thesis block.
- **Two or more tickers** → full analysis on each, a comparative snapshot table, and two explicit
  verdicts: **Best Buy Today** and **Best Long-Term Hold**.

## Contents

| File | Purpose |
|------|---------|
| `SKILL.md` | The skill definition and full 8-layer framework |
| `references/valuation-formulas.md` | DCF, WACC, ROIC, PEG, reverse-DCF formulas |
| `references/ratio-benchmarks.md` | Industry median ratios by sector |
| `references/technical-indicators.md` | Indicator definitions and interpretation rules |

## Installing as a Claude skill

Place the skill in a directory Claude discovers as a skill source — for example a personal skills
folder or a plugin's `skills/` directory:

```bash
git clone https://github.com/landenf/stock-analysis-skill.git
# copy or symlink the folder into your Claude skills location, e.g.:
cp -r stock-analysis-skill ~/.claude/skills/stock-analysis
```

The skill activates automatically whenever a request involves analyzing, valuing, or comparing a
specific equity.

## Scope

**Does:** 8-layer fundamental + technical + sentiment + price-target analysis, single and
multi-ticker comparison with explicit verdicts, valuation modeling (multiples + DCF range).

**Does not:** provide personalized investment advice, access live brokerage or real-time price feeds
(it uses web search), execute trades, size positions, or model options pricing.

## License

[MIT](LICENSE)
