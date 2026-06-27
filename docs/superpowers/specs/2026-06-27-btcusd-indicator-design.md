# Design Spec — BTCUSD Trend Indicator

**Date:** 2026-06-27  
**Status:** Approved  
**Platform:** TradingView / Pine Script v6

---

## 1. Purpose

A multi-timeframe trend-following indicator for BTCUSD. Uses a 21/50/200 EMA stack on two timeframes — 4H for trend direction, 15m for entry timing — to produce high-confluence buy/sell signals with minimal noise.

---

## 2. Architecture

Applied to the **15m BTCUSD chart**. The 4H EMA data is fetched via `request.security()` — no chart switching required.

| # | Component | Responsibility |
|---|---|---|
| 1 | MTF EMA Engine | Calculates 21/50/200 EMAs on 4H and 15m |
| 2 | Bias Logic | Labels each timeframe Bullish / Bearish / Neutral |
| 3 | Signal Generator | Fires Long/Short on confirmed bar close |
| 4 | Background Renderer | Tints chart green (bullish) or red (bearish) |
| 5 | Arrow Renderer | Plots ▲ / ▼ arrows at signal bars |
| 6 | Score Panel | Removed — overlay=true incompatible with 0-3 scale on $60k BTC |
| 7 | Dashboard Table | On-chart table: 4H bias / 15m bias / score / last signal |

---

## 3. Signal Logic

| Signal | Conditions |
|---|---|
| LONG | 4H = Bullish AND 15m 21 EMA crosses above 50 EMA AND price > 200 EMA (15m) |
| SHORT | 4H = Bearish AND 15m 21 EMA crosses below 50 EMA AND price < 200 EMA (15m) |

**No repainting:** `barstate.isconfirmed` on both signals + `lookahead=barmerge.lookahead_off`.

---

## 4. User Inputs

| Input | Default | Description |
|---|---|---|
| Fast EMA | 21 | Fast EMA period |
| Mid EMA | 50 | Mid EMA period |
| Slow EMA | 200 | Slow EMA period |
| HTF Timeframe | "240" | Higher timeframe for trend filter |
| Show Background | true | Toggle background coloring |
| Show Arrows | true | Toggle signal arrows |
| Show Table | true | Toggle dashboard table |

---

## 5. Edge Cases

- **Neutral 4H:** No signal fires. Background transparent. Table shows "Neutral" in gray.
- **Score Panel removed:** `overlay=true` pins all plots to price pane — 0–3 values invisible on $60k BTC. Scores shown in dashboard table instead.
