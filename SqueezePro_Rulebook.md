# Squeeze Pro Rulebook

This is the working rulebook for the project.

Use this file for:
- indicator interpretation
- setup selection
- entry filtering
- exit logic
- scan design

When new videos or docs are added, update this file instead of relying on memory.

## 1. Source Priority

Use sources in this order:

1. Thinkorswim source files
2. Official docs / PDFs / settings notes
3. Live-session transcript notes
4. Raw transcript only if the above do not cover it

If a noisy transcript conflicts with docs/source, trust docs/source.

## 2. Indicator Types In This Folder

### `TTM_Squeeze_Classic.pine`
- Classic TTM behavior
- `Red` zero-line dot = squeeze ON
- `Green` zero-line dot = squeeze OFF / released

### `SqueezePro_TradingView.pine`
- Squeeze Pro style lower-panel indicator
- Has:
  - multi-compression dots
  - histogram
  - legacy arrows
  - FIRE markers

### `SqueezePro_LiveChecklist_Overlay.pine`
- Price overlay companion
- Adds:
  - `8 EMA`
  - `21 EMA`
  - `34 EMA`
  - `2 ATR / 3 ATR`
  - `LONG READY`
  - `SHORT READY`
  - `WAIT PULLBACK`
  - `FIRE`
  - status table

## 3. Core Squeeze Logic

### Classic TTM squeeze
- Squeeze ON = Bollinger Bands inside Keltner Channel
- Squeeze OFF = Bollinger Bands outside Keltner Channel

### Squeeze Pro compression states
- `Black` = low compression squeeze ON
- `Red` = mid compression squeeze ON
- `Orange / dark yellow` = high compression squeeze ON
- `Green` = no squeeze / released

### Practical meaning
- Any dark dot = market is compressing
- First green dot after dark dots = squeeze released

## 4. Histogram Meaning

- Above zero and rising = bullish momentum strengthening
- Above zero and falling = bullish momentum weakening
- Below zero and falling = bearish momentum strengthening
- Below zero and rising = bearish momentum weakening / rebound

Histogram gives direction, not squeeze state.

## 5. Arrows And FIRE

### Legacy arrows
- Trigger after squeeze lasts the threshold bar count
- Default threshold from docs/source: `6`
- Direction depends on selected signal mode

### FIRE
- Marks squeeze release
- Use as the actual launch/release marker

### Important
- Arrow is not the same as release
- FIRE is not the same as early entry

## 6. Signal Direction Modes

Supported documented modes:

- `HistAboveBelowZero`
- `HistRisingFalling`
- `HistRisingFromBelowFallingFromAbove`

## 7. Live-Session Trading Rules

These are the practical trade filters taken from the live session after removing noise.

### 7.1 Market context
- They start with broad market context first
- In the live session:
  - put/call ratio
  - skew
- This is a directional context filter, not a direct trigger

### 7.2 Mean concept
- `21 EMA` is treated as the mean
- Preferred trades are near the mean, not after large extension

### 7.3 Trend concept
- `8 EMA` and `34 EMA` are the main trend filter

Long trend:
- `8 > 34`
- ideally both rising

Short trend:
- `8 < 34`
- ideally both falling

### 7.4 Preferred price location
- Prefer price in the zone between `8 EMA` and `34 EMA`
- If price is too stretched away from the mean:
  - wait
  - reduce size
  - or ignore

### 7.5 Clean vs messy
- Clean setup = trend, histogram, squeeze, and location agree
- Messy setup = mixed signals or awkward structure
- If setup is messy, skip it

## 8. Long Checklist

A high-quality long candidate should ideally have:

1. Squeeze exists or is setting up
2. Long-supportive arrow / early setup / FIRE context
3. `8 EMA > 34 EMA`
4. Histogram supportive
5. Price near mean or inside the `8/34` zone
6. Setup looks clean

## 9. Short Checklist

A high-quality short candidate should ideally have:

1. Squeeze exists or is setting up
2. Short-supportive arrow / early setup / FIRE context
3. `8 EMA < 34 EMA`
4. Histogram bearish
5. Price near mean or inside the `8/34` zone
6. Setup looks clean

## 10. Entry Preference

Preferred:
- enter near the mean
- enter in the `8/34` zone
- enter before major extension

Avoid:
- chasing after price is already stretched
- taking arrows with no trend alignment

## 11. Exit / Trade Management

Working baseline from the session:

- scale out around `2 ATR`
- scale out more around `3 ATR`
- if the original reasons for the trade are no longer true, exit
- smaller position size is preferred to oversized risk

## 12. Multi-Timeframe Rule

- Always know which timeframe you are trading
- If trading daily, weekly is more useful confirmation than a 5-minute chart
- A lower timeframe can show a temporary move against the higher timeframe

## 13. What To Ignore

Ignore:
- platform install/import chatter
- TradeStation-specific formatting noise
- scanner UI chatter that does not affect rules
- raw transcript mistakes

## 14. Scanning Workflow

There are two practical scanning paths for you:

### Path A: TradingView Pine Screener
- Best when you want to scan your own Pine scripts directly
- Works on watchlists
- Use your own script plots or alert conditions as filters

### Path B: Chartink
- Best when you want NSE stock scans and simple custom formulas
- Good for prefiltering candidates
- Final confirmation can then happen on TradingView

## 15. How To Scan In TradingView

Based on TradingView Pine Screener docs:
- it scans watchlists with Pine scripts
- it can use your own favorite indicator
- filters can be based on `plots` or `alertcondition()` outputs

Working method:

1. Save your Pine script
2. Add it to favorites in TradingView
3. Open `Products -> Screeners -> Pine`
4. Choose your watchlist
5. Choose the indicator
6. Filter on plots or alert conditions
7. Scan

### Important TradingView constraints
- one indicator per screen
- script must expose at least one `plot()` or `alertcondition()`
- only supported screener timeframes
- custom inputs are limited

### Best use for TradingView in this project
- Scan `SqueezePro_TradingView.pine` or a scan-specific version
- Filter for:
  - squeeze on
  - squeeze just fired
  - long ready
  - short ready
  - wait pullback

## 16. How To Scan In Chartink

Based on Chartink docs:
- you can create custom / derived indicators
- those custom indicators can be reused in scans
- timeframe can be selected for those indicators

### Best practical approach in Chartink

Use Chartink as a prefilter, not as the final full Squeeze Pro engine.

Build scans for:
- low volatility compression
- Bollinger/Keltner relationship
- trend filter
- price near moving average
- volume filter

Then verify on TradingView with the Pine scripts.

## 17. Recommended Scan Logic

### 17.1 Chartink prefilter for long candidates

Use these ideas:
- Bollinger Bands narrow / inside Keltner-style condition
- close above 8 EMA
- 8 EMA above 34 EMA
- close near 21 EMA
- volume above recent average

### 17.2 Chartink prefilter for short candidates

Use these ideas:
- squeeze / low volatility condition
- close below 8 EMA
- 8 EMA below 34 EMA
- close near 21 EMA
- volume above recent average

### 17.3 TradingView confirmation

Confirm using our Pine scripts:
- active squeeze?
- released now?
- trend aligned?
- extended or not?
- clean or messy?

## 18. Working Scanning Plan For You

### For Chartink
Use it to find:
- stocks near compression
- stocks with 8/34 alignment
- stocks near the mean

### For TradingView
Use Pine Screener or watchlists to confirm:
- classic squeeze state
- Squeeze Pro state
- live checklist state

## 19. Future Research Workflow

When you add more videos:

1. extract transcript
2. write a cleaned note
3. update this rulebook
4. only then change scripts

## 20. Current Bottom Line

Our current working interpretation is:

- classic TTM tells us squeeze ON/OFF
- Squeeze Pro tells us squeeze strength + histogram + arrow/release behavior
- live-session rules tell us whether a squeeze is actually tradable
