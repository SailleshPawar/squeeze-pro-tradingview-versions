# Live Trading Session Notes (2019-06-05)

Source video:
- `C:/Users/hp/Downloads/Simpler Trading - Squeeze Pro System Premium/Squeeze Pro Part 1/2 Pro Live-Trading Days/rec-2019-06-05_08.32.40.mp4`

Transcript files:
- `C:/Users/hp/Downloads/OiChartEra/Live_Trading_2019-06-05_Transcript.txt`
- `C:/Users/hp/Downloads/OiChartEra/Live_Trading_2019-06-05_Transcript.json`

Note:
- Transcript was auto-generated locally and is noisy in places, but the trading logic is clear enough.

## What They Are Actually Doing

### 1. They start with market context before any stock setup
- Around `00:03:00 - 00:12:00`
- They first read the market using:
  - 10-day moving average of the combined equity/index put-call ratio
  - skew
- Their point is simple:
  - when everyone is too short, expect short-covering rallies
  - when everyone is too long, expect selloffs
- This is used as a top-down bias filter, not as a direct entry signal.

### 2. They frame trades around the mean
- Around `00:12:00 - 00:15:00` and `01:06:00 - 01:12:00`
- They use:
  - `21 EMA` as the mean
  - `ATR bands` around the mean for stretch and target context
- He says there are only two trades:
  - trade at the mean expecting expansion away from it
  - trade away from the mean expecting reversion back to it
- Squeeze setups are his preferred way to trade the first type.

### 3. They do not take every squeeze
- Around `00:15:00 - 00:24:00` and `01:30:00 - 01:36:00`
- He keeps judging setups as `clean` or `messy`.
- Core idea:
  - if the chart is confusing, skip it
  - if you have to stare at it too long, it is not a trade
- He explicitly says:
  - if there is no squeeze, he usually does not want to look at it
  - he prefers an `actionable signal`, not random chart patterns

### 4. Their long checklist
- Spread across `00:18:00 - 00:24:00`, `01:33:00 - 01:39:00`, `02:09:00 - 02:12:00`
- Practical long conditions from the session:
  - squeeze present
  - buy arrow after enough dots
  - `8 EMA` above `34 EMA`
  - ideally both are rising
  - histogram above zero, or at least not deeply conflicting
  - price preferably between the `8` and `34`
  - entry as close to the mean as possible
- He likes getting in before the actual squeeze release if the setup is clean.

### 5. Their short checklist
- Clearest explanation at `02:12:00 - 02:15:00`
- For the ideal short:
  - price below the `34` and above the `8`
  - squeeze histogram below zero
  - `8 EMA` crossed below `34 EMA`
  - down arrow prints
- If all of that is true at the arrow, they take the bearish trade.
- They used `SQ` as the live example.

### 6. They prefer buying pullbacks, not chasing extension
- Around `00:24:00 - 00:30:00`, `01:36:00 - 01:39:00`, `02:39:00 - 02:42:00`
- This is probably the biggest practical takeaway.
- He repeatedly avoids buying stocks that are already stretched.
- Preferred entry:
  - between the `8` and `34`
  - near the `21 EMA`
  - or on a pullback toward the mean
- If a stock is extended:
  - either skip it
  - or go `half size`
  - or place a lower limit order to buy a pullback

### 7. They use the squeeze as an early entry tool, not just a release tool
- Around `00:18:00 - 00:21:00`, `01:33:00 - 01:39:00`, `02:09:00 - 02:12:00`
- The logic is:
  - buy when the setup is lining up
  - let later traders chase after the squeeze fully fires
- He compares this to buying inventory early and selling it later when demand shows up.

### 8. They trade different timeframes differently
- Around `01:24:00 - 01:30:00` and `02:15:00 - 02:21:00`
- Important rule:
  - know which timeframe you are trading
- He says:
  - a `5-minute` squeeze may last `35 to 45 minutes`
  - a `daily` squeeze may last `7 to 10 days`
- He is fine with:
  - a short signal on the daily chart
  - a temporary long signal on the 5-minute chart
- Reason:
  - they are different trades with different holding periods
- Confirmation rule:
  - if trading the daily, look to the weekly for confirmation
  - check the chart above, not the chart below

### 9. They manage trades by scaling out and by condition failure
- Around `02:21:00 - 02:36:00`
- Exit/risk rules discussed in the session:
  - trade smaller so you do not need oversized stops
  - if the conditions that got you into the trade are no longer true, exit
  - scale out at `2 ATR`
  - scale out more at `3 ATR`
  - final exit when histogram/momentum rolls over
- He explicitly prefers position sizing over taking oversized option risk.

## Live Examples They Used

### `V`
- Around `00:18:00 - 00:24:00`
- He liked it on the long side because:
  - daily squeeze
  - early warning active
  - trend still positive
- He bought July in-the-money call options.

### `BOOM`
- Around `00:24:00 - 00:30:00`
- He liked the trend but said it was too extended to buy immediately.
- He set a lower buy order for a pullback instead of chasing it.

### `SQ`
- Around `01:18:00 - 01:24:00` and `02:12:00 - 02:15:00`
- This is his best live bearish example in the session.
- Why he liked it:
  - bearish trend structure
  - squeeze/arrow criteria aligned
  - fit the short checklist
- He bought puts.

### `SHOP`
- Around `00:15:00 - 00:18:00` and `02:30:00 - 02:33:00`
- He calls it one of the cleanest examples.
- But he still does not want to chase it after it becomes too extended.

## What To Improve In Your TradingView Indicator Based On This Session

### High priority
- Add a clear `clean vs messy` checklist label:
  - long clean
  - short clean
  - conflict / messy
- Mark `between 8 and 34` as a separate state.
- Mark whether `8 > 34` or `8 < 34` clearly.
- Add a `near mean / extended` status using distance from `21 EMA` or ATR.

### Useful additions
- Add `2 ATR` and `3 ATR` target bands.
- Add a label like:
  - `LONG READY`
  - `SHORT READY`
  - `EXTENDED - WAIT PULLBACK`
- Add higher timeframe confirmation if you want to follow the session more closely.

### Most important simplification
- Do not rely on the dots alone.
- In the live session, they are combining:
  - squeeze state
  - arrow
  - histogram direction
  - 8/34 trend
  - entry location relative to the mean

