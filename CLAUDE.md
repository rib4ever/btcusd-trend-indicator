# Project: BTCUSD Trend Indicator

## Project Identity
- Project ID: btcusd-trend-indicator
- Path: `_projects/btcusd-trend-indicator/`
- Type: Pine Script v6 / TradingView Indicator
- Status: Active

## Purpose
A multi-timeframe trend-following indicator for BTCUSD on TradingView. Uses a 21/50/200 EMA stack across 4H (trend filter) and 15m (entry signal), with buy/sell arrows, background bias coloring, an on-chart dashboard table, and alerts.

## Before Working
- Read `PROJECT_CONTEXT.md` and `PROJECT_ROADMAP.md`.
- Check `CHANGELOG.md` (latest) and `TODO.md`.
- Main source file: `src/btcusd_trend_indicator.pine`
- Design spec: `docs/superpowers/specs/2026-06-27-btcusd-indicator-design.md`

## Project Rules
- All Pine Script changes must be tested on TradingView before marking done.
- No repainting: all signals on confirmed bar close only.
- `request.security()` must use `lookahead=barmerge.lookahead_off`.
- Secrets/API keys live in `.env` (git-ignored). Never commit secrets.

## Validation (before "done")
- Test indicator on BTCUSD 15m chart on TradingView.
- Verify no repainting on historical bars.
- Update `CHANGELOG.md` and `TODO.md`/roadmap.
