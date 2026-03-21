# Squeeze Pro Research Baseline

This file is the clean reference for the work done today.

Use this as the source of truth going forward.
Ignore noisy transcript segments, platform troubleshooting chatter, and auto-transcription mistakes unless they are directly confirmed by the docs or source files.

## Primary Sources

### Documentation and source
- `C:/Users/hp/Downloads/Simpler Trading - Squeeze Pro System Premium/Squeeze Pro Part 1/SimplerTrading - SQUEEZE BASIC SYSTEM (TOS)/Squeeze Pro - Available Platforms ThinkorSwim, Tradestation/Supporting Documentation/What is the Squeeze Pro.docx`
- `C:/Users/hp/Downloads/Simpler Trading - Squeeze Pro System Premium/Squeeze Pro Part 1/SimplerTrading - SQUEEZE BASIC SYSTEM (TOS)/Squeeze Pro - Available Platforms ThinkorSwim, Tradestation/Supporting Documentation/SqueezePROTos.pdf`
- `C:/Users/hp/Downloads/Simpler Trading - Squeeze Pro System Premium/Squeeze Pro Part 1/SimplerTrading - SQUEEZE BASIC SYSTEM (TOS)/Squeeze Pro - Available Platforms ThinkorSwim, Tradestation/Supporting Documentation/SqueezePRO_SignalsTOS.pdf`
- `C:/Users/hp/Downloads/Simpler Trading - Squeeze Pro System Premium/Squeeze Pro Part 1/Squeeze Pro Indicators/Indicators import/ST_SqueezePROSTUDY.ts`
- `C:/Users/hp/Downloads/Simpler Trading - Squeeze Pro System Premium/Squeeze Pro Part 1/Squeeze Pro Indicators/Indicators import/ST_SqueezePRO_SignalsSTUDY.ts`
- `C:/Users/hp/Downloads/Simpler Trading - Squeeze Pro System Premium/Squeeze Pro Part 1/Squeeze Pro Indicators/Indicator Files/SqueezePRO Scan and Settings.txt`

### Extracted transcript references
- `C:/Users/hp/Downloads/OiChartEra/Indicator_Session_Transcript.txt`
- `C:/Users/hp/Downloads/OiChartEra/Live_Trading_2019-06-05_Transcript.txt`
- `C:/Users/hp/Downloads/OiChartEra/Live_Trading_2019-06-05_Notes.md`

## High-Confidence Rules

### 1. Classic TTM Squeeze
- Single-state squeeze.
- `Red` dot on zero line = squeeze ON.
- `Green` dot on zero line = squeeze OFF / released.
- No low/mid/high compression breakdown.

### 2. Squeeze Pro squeeze states
- `Black` = low compression squeeze ON.
- `Red` = mid compression squeeze ON.
- `Orange / dark yellow` = high compression squeeze ON.
- `Green` = no squeeze / squeeze released.

### 3. Core mechanical squeeze logic
- Squeeze ON = Bollinger Bands are inside the Keltner Channel.
- Squeeze OFF / fired = Bollinger Bands move back outside the Keltner Channel.
- The histogram provides directional context.

### 4. Histogram color intent
- Above zero and rising = stronger bullish momentum.
- Above zero and falling = weakening bullish momentum.
- Below zero and falling = stronger bearish momentum.
- Below zero and rising = weakening bearish momentum / recovery.

### 5. Signals vs FIRE
- Legacy arrows are not the same as squeeze release.
- Legacy arrows appear after the required squeeze-bar count, default `6`.
- `FIRE` means squeeze release on that bar with directional confirmation.

### 6. Signal direction modes
- `HistAboveBelowZero`
- `HistRisingFalling`
- `HistRisingFromBelowFallingFromAbove`

These are documented and also confirmed in the Thinkorswim source.

## Live Session Trading Interpretation

This is the clean part of the live session after removing noise.

### 1. They do not trade every squeeze
- They filter setups as `clean` or `messy`.
- If the chart is confusing, they skip it.
- If there is no actionable squeeze/signal, they usually do not care about the chart.

### 2. They use context first
- Market context matters.
- In the live session he starts with broad market positioning using put/call ratio and skew.
- This is a bias filter, not a direct signal.

### 3. They trade around the mean
- `21 EMA` is treated as the mean.
- They also use ATR bands around the mean.
- Preferred entries are near the mean, not after a large extension.

### 4. Trend filter
- `8 EMA` and `34 EMA` are a major decision filter.
- Long bias:
  - `8 > 34`
  - ideally both rising
- Short bias:
  - `8 < 34`
  - ideally both falling

### 5. Preferred entry location
- Prefer price between the `8` and `34` EMA zone.
- If price is too stretched away from the mean, they usually wait for a pullback or reduce size.

### 6. Long checklist from the session
- Squeeze setup exists.
- Arrow/signal exists or early warning is present.
- `8 EMA > 34 EMA`
- Histogram is supportive.
- Price is near the mean / in the EMA zone.
- Setup should look clean, not messy.

### 7. Short checklist from the session
- Squeeze setup exists.
- Down arrow/signal exists.
- `8 EMA < 34 EMA`
- Histogram is bearish.
- Price is near the mean / in the EMA zone.
- Setup should look clean, not messy.

### 8. Multi-timeframe rule
- Always know which timeframe you are trading.
- If trading the daily chart, the weekly chart is a better confirmation frame than the 5-minute chart.
- Shorter timeframe signals can exist inside a larger opposite-direction trade.

### 9. Exit / management concepts
- Scale out around `2 ATR` and `3 ATR`.
- If the conditions that got you into the trade are no longer true, exit.
- They prefer smaller size over oversized risk.

## Important Distinctions

### Early Entry is not the same thing as Squeeze Pro
- `Early In and Out Pro` is a separate concept/tool from the base Squeeze Pro.
- It tries to anticipate the squeeze firing by watching BB behavior before full release.
- Do not mix this up with the standard squeeze dots/arrows.

### Arrows do not equal trade command by themselves
- The live session uses arrows plus:
  - trend structure
  - histogram
  - mean location
  - clean vs messy judgment

## Noise To Ignore

Ignore these unless directly relevant:
- platform install/import issues
- TradeStation vs Thinkorswim UI discussion
- scanner setup chatter
- mobile platform limitations
- transcript wording glitches from auto-transcription
- Q&A noise that does not change the core rules

## Practical Working Baseline For Our Pine Scripts

### `TTM_Squeeze_Classic.pine`
- Use for plain old TTM style red/green squeeze state only.

### `SqueezePro_TradingView.pine`
- Use for lower-pane Squeeze Pro style dots, histogram, legacy arrows, and FIRE.

### `SqueezePro_LiveChecklist_Overlay.pine`
- Use for the filtered live-session interpretation:
  - trend
  - mean
  - extension
  - ready/wait/fire context

## Current Working Principle

When there is disagreement between noisy transcript text and the clearer source/doc behavior:
- trust the docs/source first
- use the live-session transcript only for trade interpretation and workflow
- ignore unconfirmed noise
