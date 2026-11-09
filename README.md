# Binance Futures Scanner PRO — Full Android Project with 30-Day Backtesting

Android Studio project wrapping the full scanner in Android WebView.

## Build APK
1. Open this folder in Android Studio (JDK 17, Android SDK 35).
2. Allow Gradle sync.
3. Select Build > Build Bundle(s) / APK(s) > Build APK(s).
4. Debug APK path: `app/build/outputs/apk/debug/app-debug.apk`.

## Features
- Binance USDⓈ-M public market scanner (no API keys)
- 5-day growth, 5m RVOL, EMA 9/21/50, VWAP
- 15m / 1h trend context, OI, taker-volume delta proxy, BTC filter
- Early bullish candlestick and chart-structure candidates
- Breakout / retest signals, ranking and risk planner
- 30-day historical backtesting on 15m klines for selected USDT-M symbols
- Pattern-wise signal counts, wins, losses, expired outcomes and hit rate
- No automatic orders, no account access

## Backtest methodology / limitations
- Signal detection uses only candles available up to each signal close (no look-ahead in pattern detection).
- Outcome test checks a configurable upside target and downside stop over a configurable number of future 15m candles. If target and stop are both touched in one candle, stop is counted first.
- Hit rate = wins / (wins + losses); expired outcomes are shown separately and excluded from hit-rate denominator.
- This is a simplified long-only OHLCV test, not a full strategy backtest. It excludes fees, slippage, funding, spread, liquidation, leverage, order-book liquidity and execution delay.
- Pattern rules are heuristic; results are historical and do not guarantee future performance.
- Historical 30-day fetch may be rate-limited or blocked by Binance regional/network/CORS restrictions. Reduce the symbol list if needed.
- Requires internet and the app must remain open. No background push notifications are included.
- APK has not been compiled or signed in this environment; build it in Android Studio.
