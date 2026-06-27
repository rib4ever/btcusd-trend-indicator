# BTCUSD MTF EMA Trend Indicator

Pine Script v6 multi-timeframe trend-following indicator for BTCUSD on TradingView. Uses a 21/50/200 EMA stack across 4H (trend filter) and 15m (entry signals) with no-repaint signals, background bias coloring, an on-chart dashboard table, and TradingView alerts.

## Quick start

1. Open TradingView Pine Editor
2. Paste `src/btcusd_trend_indicator.pine`
3. Add to BTCUSD 15m chart
4. Configure alerts using the built-in `alertcondition` triggers

## Features

- **Multi-timeframe:** 4H trend filter + 15m entry signals
- **EMA Stack:** 21 / 50 / 200 EMA alignment (Bullish / Bearish / Neutral)
- **No-repaint:** all signals fire on confirmed bar close (`barstate.isconfirmed`)
- **Visual:** background bias coloring + ▲/▼ entry arrows
- **Dashboard table:** top-right panel showing 4H & 15m bias, score, and last signal
- **Alerts:** Long and Short `alertcondition` triggers built in

## Structure

| Folder | Purpose |
|---|---|
| `src/` | Pine Script source file |
| `docs/` | Design spec and implementation plan |
