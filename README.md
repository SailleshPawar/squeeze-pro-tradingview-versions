# Squeeze Pro TradingView Versions

This repo contains local TradingView/Pine recreations and notes derived from the Simpler Trading Squeeze Pro materials.

## Files

- `SqueezePro_TradingView.pine`
  - Lower-pane Squeeze Pro style recreation with squeeze dots, histogram, legacy arrows, and FIRE markers.

- `TTM_Squeeze_Classic.pine`
  - Classic single-state TTM Squeeze style version.
  - `Red` zero-line dots = squeeze on
  - `Green` zero-line dots = squeeze off

- `SqueezePro_LiveChecklist_Overlay.pine`
  - Overlay companion based on the live trading session.
  - Adds:
    - `8 / 21 / 34 EMA`
    - `2 ATR / 3 ATR` context bands
    - `LONG READY` / `SHORT READY`
    - `WAIT PULLBACK`
    - `FIRE`
    - a top-right status table

- `Live_Trading_2019-06-05_Notes.md`
  - Cleaned notes extracted from the live-trading video.

## Suggested Usage

Use both indicators together:

1. Add `SqueezePro_TradingView.pine` to keep the classic lower-panel squeeze view.
2. Add `SqueezePro_LiveChecklist_Overlay.pine` on price to filter setups.
3. Add `TTM_Squeeze_Classic.pine` if you want the original simpler red/green TTM-style squeeze state.

## Important Note

These scripts are behavioral recreations based on documentation, source snippets, and session review. They are not guaranteed to be exact proprietary ports.
