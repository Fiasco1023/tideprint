# Tideprint Pine v6.2

Successor to Wen2Trade. Overlay confluence for crypto.

Copy the **raw** `.pine` file. Do not paste from chat or from a scrolled preview — that is how the 162-error fragment (`Undeclared identifier showVWAP` / `ema1`) happens.

## How to paste into TradingView

The editor tab named **Tideprint 08202026** is a truncated paste (plots glued onto the inputs). Do not keep fixing that file. It is missing the calculation block.

1. Open the raw file: https://raw.githubusercontent.com/Fiasco1023/tideprint/main/tideprint.pine
2. Ctrl+A, Ctrl+C (the whole page — about 518 lines)
3. TradingView → Pine Editor → Open → **New blank indicator**
4. Ctrl+A, Ctrl+V into the blank script
5. Check the line counter is **~518**. You must see:
   - line 18: `indicator("Tideprint"`
   - line 44: `bool showVWAP`
   - line 394: `plot(showVWAP ? vwapVal`
6. Save, then Add to chart. Problems panel should be **0**.

If `plot(showVWAP` sits near line 49, it is still the fragment. Delete that tab and start from a new blank indicator.

## Files

| File | What |
| --- | --- |
| [tideprint.pine](https://github.com/Fiasco1023/tideprint/blob/main/tideprint.pine) | Full v6.2 script — ST Long is original Super Long (purple L) (labels instead of plotshape, plot-count ~30 / 64) |

## v6.2 — ST Long is the original Super Long

Wen2Trade's plotted Super Long was `STLong` (purple **L**), not the MACD `SUPERLONG` print.

ST Long now fires when:

- CCI (50) crosses above 0
- fast HMA (6) is above mid HMA (12)
- fast HMA is above SuperTrend 1, 2, and 3
- bull candle (close > open)

Removed: HTF CCI gate, all-three SuperTrend *direction* flag, shared 5-bar cooldown (those were eating daily BTC prints).
