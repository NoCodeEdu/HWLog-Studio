# HWLog Studio

A single-file, offline viewer for [HWiNFO](https://www.hwinfo.com/) sensor logs. Open a CSV log, search hundreds of sensors, stack synced charts, zoom into moments, and save the data together with your layout in one file.

No install, no server, no build step. Everything runs locally in your browser, and nothing is uploaded.

## Getting started

1. Download `HWLog-Studio.html`.
2. Open it in a current version of Chrome, Edge, Firefox or Safari.
3. Drop a HWiNFO `.CSV` log onto the page, or click **Choose file**.

To record a log, open HWiNFO's Sensors window, click **Logging Start**, and save as `.CSV`.

When a log opens, HWLog Studio builds an automatic dashboard from its sensors (temperatures, CPU/GPU load, clocks, power, frame rate, memory, fans).

### EXAMPLE: https://nocodeedu.github.io/HWLog-Studio/HWLog-Studio.html

## Features

- **Sensor panel**: search, filter by unit, group by device or unit, hide constant sensors, with a sparkline and peak value for every sensor.
- **Synced charts**: any number of charts with a shared cursor and zoom. Drag to reorder, stretch to full width, or open one full screen.
- **Mixed units**: a sensor with a different unit goes to a new chart, or onto a right axis.
- **Chart tuning**: axis ranges, log scale, line style, smoothing, fill, average lines and threshold lines. Each sensor can also have its own colour, label, dash and scale/offset.
- **Quick charts**: one-click templates for per-core temps and clocks, per-thread usage, CPU limits, GPU, drives, network and throttling flags.
- **Dashboards**: keep several dashboards per log, and create, duplicate, rename or switch between them.
- **Overview strip**: a mini chart of the whole log. Drag a window across it to zoom and pan.
- **Markers**: label moments such as "race start" or "stutter", then zoom between them.
- **Summary view**: tiles for peaks and averages, Yes/No flags that were raised (e.g. throttling), and a sortable min / avg / max / std-dev table for the current range.
- **Data view**: the raw samples as a scrolling table, with the chart cursor's row highlighted.
- **Dark and light themes.**

## Saving

| Option | What it saves |
|---|---|
| **Save session** | One `.hwls` file with the log data plus every dashboard, chart, marker, filter and setting. Open it later to pick up where you left off. |
| **Save layout only** | A small `.hwls` template with no data. Open it with another log to reuse your charts. Sensors are matched by name. |

`.hwls` files are gzip-compressed JSON. The browser also remembers your last layout and offers to resume your last log. You can clear both in **Settings**.

## Exports

- The original CSV, or a trimmed CSV of the current time range (plotted sensors or the sensor panel filter) in HWiNFO's format.
- The statistics table as CSV.
- A single chart or the whole dashboard as PNG.
- Values at a moment (right-click a chart) or a chart's statistics, copied to the clipboard.

## Controls

| Key | Action |
|---|---|
| `/` | Search sensors |
| `N` | New chart |
| `M` | Add a marker at the cursor |
| `0` | Reset zoom |
| `+` / `−` | Zoom in / out |
| `←` / `→` | Pan |
| `1`–`4` | Charts per row |
| `F` / `Esc` | Full screen for the active chart / back |
| `T` | Toggle theme |
| `?` | Help |
| `Ctrl/⌘ + S` | Save session |
| `Ctrl/⌘ + O` | Open a file |

**Mouse:** drag across a chart to zoom, and double-click to reset. `Ctrl/⌘ + wheel` zooms, `Shift + wheel` pans, and right-click opens markers and zoom presets.

**Sensors:** click a sensor to add it to or remove it from the active chart, or double-click it to start a new chart. Ctrl/⌘-click or Shift-click selects several. You can also drag sensors onto a chart.

## Search syntax

| Example | Meaning |
|---|---|
| `core temp` | All words must match |
| `clock -effective` | Exclude a word |
| `"gpu power"` | Exact phrase |
| `unit:°C` `group:gpu` `name:fan` | Field filters (short forms: `u:` `g:` `n:`) |
| `/core \d+ t1/` | Regular expression |

## Supported files

- HWiNFO CSV logs, separated by commas, semicolons or tabs, in UTF-8 or Windows-1252. Other CSVs with numeric columns also open.
- `.hwls` sessions and layouts.
- Gzipped versions of either.

## Credits

Charts are drawn with [uPlot](https://github.com/leeoniya/uPlot) by Leon Sorokin (MIT license), which is bundled inside the HTML file.
