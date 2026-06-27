# Project Context — BTCUSD Trend Indicator

## Background
Ravi wants a TradingView Pine Script v6 indicator to trade BTCUSD using a multi-timeframe EMA stack approach. The indicator filters trend on the 4H and takes entries on the 15m, producing high-confluence signals with minimal noise.

## Scope
- In scope: Pine Script v6 indicator file, EMA stack logic (21/50/200), MTF trend filter (4H), entry signals (15m), background coloring, arrows, dashboard table, TradingView alerts.
- Out of scope: Python backtesting, live trading execution, broker integration, mobile apps.

## Constraints & Assumptions
- Platform: TradingView (Pine Script v6).
- Primary chart timeframe: 15m. 4H data via `request.security()`.
- No repainting: signals fire on confirmed bar close only.
- `request.security()` uses `lookahead=barmerge.lookahead_off`.
- EMA periods (21/50/200) are user-configurable inputs.
- Works on TradingView free plan (no paid features required).

## Key Resources
- Design spec: `docs/superpowers/specs/2026-06-27-btcusd-indicator-design.md`
- Main source: `src/btcusd_trend_indicator.pine`

## Current State
v1.1.0 — Pine Script v6 indicator complete. All 7 components implemented. Awaiting manual TradingView validation.
