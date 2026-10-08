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
| **Buy % / Sell %** | Multi-factor 0–100 confidence shown live in the table |
| **Alerts** | Three built-in alert conditions (BUY / SELL / Any Signal) |

### Scalping Mode (1m – 5m)

The default **Profile = Auto** picks faster EMA / RSI / MACD / Stoch / ATR settings and a signal cooldown from the chart timeframe (1m, 3m, 5m; anything higher uses the 5m set). Choose **Manual** to use your own inputs.

| Profile | EMA (fast/mid/slow) | RSI | MACD | ATR | Cooldown |
|---|---|---|---|---|---|
| 1m | 8 / 21 / 55 | 7 | 6-13-5 | 10 | 3 bars |
| 3m | 9 / 21 / 55 | 9 | 8-17-6 | 12 | 2 bars |
| 5m | 9 / 21 / 50 | 10 | 8-21-7 | 14 | 2 bars |

Other defaults: Min Confidence 58%, Min ATR 0.015% of price, SL 1.2×ATR, TP1 1.2×ATR, TP2 2.4×ATR, volume filter off. Works on XAUUSD and BTCUSD (if signals are too many/few on BTC, adjust *Min Confidence* and *Min ATR %*).

### Signal Logic

**BUY** fires when all of these are true on a **closed** bar:
1. Fast EMA > Mid EMA and close > Mid EMA
2. RSI between 45 and the overbought level (75)
3. At least one trigger: MACD cross up, Stoch RSI K cross above D (K < 85), or close crossing above the fast EMA
4. Buy % ≥ Min Confidence, ATR filter passed, cooldown elapsed (and optional volume filter)

**SELL** is the mirror image (Sell % ≥ Min Confidence, RSI 25–55, etc.).

Compared with the old slow logic (price above all EMAs **and** MACD cross **and** Stoch cross at once), only one trigger is needed, so signals are noticeably more frequent while the trend, confidence, ATR and cooldown filters limit noise.

### Reading Buy % / Sell %

Shown in the on-chart table (and in the Data Window / status line). Built from three factors, each scored −1…+1, weighted (default 40 / 40 / 20) and mapped to 0–100:
- **Trend** – EMA stack, price vs slow EMA, fast-EMA slope
- **Momentum** – RSI, MACD histogram (relative to ATR), Stoch RSI
- **Volatility / volume** – candle body in ATR units, boosted by relative volume

Buy % + Sell % = 100. **≥ 60%** = clear lean; **45–55%** = no edge, stay out; **≥ 70%** = strong alignment. Values change every bar.

### No-Repaint Notes

Signals require `barstate.isconfirmed` (fire at bar close only), indicators use current/past bars only, and daily pivots use the previous completed day.

### How to Use

1. Open [TradingView](https://www.tradingview.com) and open an **XAUUSD** (or BTCUSD) chart on 1m, 3m or 5m.
2. Click **Pine Script Editor** at the bottom of the page.
3. Paste the full contents of `neXQan_XAUUSD_Indicator.pine`.
4. Click **Add to chart** and keep Profile = Auto.
5. More signals: lower *Min Confidence* to 55 or cooldown to 1 (Manual). Fewer/cleaner: raise *Min Confidence* to 65+.

### Recommended Timeframes

| Timeframe | Style |
|---|---|
| M1 / M3 / M5 | Scalping (tuned presets) |
| M15 / M30 | Fast intraday (uses 5m preset; consider Manual) |
| H1 / H4   | Intraday / Swing (use Manual with slower lengths) |

### Risk Disclaimer

> This indicator is for **educational purposes only** and does not constitute financial advice.  
> Always use proper risk management and never risk more than you can afford to lose.  
> Past performance of signals does **not** guarantee future results.
