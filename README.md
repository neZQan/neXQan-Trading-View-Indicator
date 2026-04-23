# neXQan Trading View Indicators

All indicators I create — Good Luck with your trading! 🚀

---

## neXQan XAUUSD Gold Indicator  (`neXQan_XAUUSD_Indicator.pine`)

A comprehensive **Pine Script v5** overlay indicator designed specifically for **Gold / XAUUSD** to improve win-rate and profitability.

### Features

| Feature | Details |
|---|---|
| **EMA Trend Filter** | 21 / 50 / 200 EMA ribbon with colour-coded shading (teal = bullish, red = bearish) |
| **RSI Filter** | Prevents entries in over-extended conditions |
| **MACD Confirmation** | Signals only fire on MACD crossovers aligned with the trend |
| **Stochastic RSI** | Adds a momentum cross-confirmation layer |
| **ATR Risk Management** | Dynamically places Stop-Loss, TP1, and TP2 labels based on market volatility |
| **Daily Pivot Points** | Classic R1/R2/R3 and S1/S2/S3 levels drawn directly on the chart |
| **Volume Filter** | Optional above-average volume confirmation (off by default, toggle per preference) |
| **Win-Rate Table** | Live on-chart table showing Overall / Buy / Sell win-rates and total signal count |
| **Bar Colouring** | Candles are highlighted green on BUY bars and red on SELL bars |
| **Alerts** | Three built-in alert conditions (BUY / SELL / Any Signal) |

### Signal Logic

**BUY** — all of the following must be true simultaneously:
1. Close above EMA 21, 50 *and* 200 (bullish structure)
2. RSI between 50 and 70 (trending up, not overbought)
3. MACD line crosses *above* signal line (momentum confirmation)
4. Stochastic RSI K crosses *above* D (and K < 80)

**SELL** — mirror conditions:
1. Close below EMA 21, 50 *and* 200 (bearish structure)
2. RSI between 30 and 50 (trending down, not oversold)
3. MACD line crosses *below* signal line (momentum confirmation)
4. Stochastic RSI K crosses *below* D (and K > 20)

### How to Use

1. Open [TradingView](https://www.tradingview.com) and open any **XAUUSD** chart.
2. Click **Pine Script Editor** at the bottom of the page.
3. Paste the full contents of `neXQan_XAUUSD_Indicator.pine`.
4. Click **Add to chart**.
5. Tune the inputs (EMA lengths, ATR multipliers, etc.) to match your preferred timeframe.

### Recommended Timeframes

| Timeframe | Style |
|---|---|
| M15 / M30 | Scalping |
| H1 / H4   | Intraday / Swing |
| D1        | Position trading |

### Risk Disclaimer

> This indicator is for **educational purposes only** and does not constitute financial advice.  
> Always use proper risk management and never risk more than you can afford to lose.  
> Past performance of signals does **not** guarantee future results.
