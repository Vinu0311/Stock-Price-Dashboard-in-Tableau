# Stock-Price-Dashboard-in-Tableau
Interactive Tableau dashboard analyzing daily price, volume, and trend data for 120 large-cap U.S. stocks — leaderboard rankings, moving-average price trends, sector breakdowns, and volume analysis.


# 📈 Stock Market Analysis Dashboard (Tableau)

An interactive Tableau workbook that analyzes daily price, volume, and trend data for 120 large-cap U.S. stocks across every major sector — built to explore performance, momentum, and volatility side by side.

## Overview

This project turns a daily OHLCV (Open/High/Low/Close/Volume) dataset into a four-view Tableau dashboard covering:

- **Relative performance** across all tickers
- **Price trend & moving averages** for an individual stock
- **Sector-level breakdowns** by market cap / ticker
- **Trading volume** patterns over time

It's designed as a self-contained exploration tool — pick a ticker, and every view updates to tell you how it's trading, how it compares to its peers, and whether it's trending up, down, or sideways.

## Dashboard / Worksheets

| Sheet | Chart Type | What it shows |
|---|---|---|
| **Leaderboard** | Bar chart | Indexed return (base 100) for every ticker, ranked to show relative winners and losers |
| **Price Trend** | Line chart | Daily price movement over time, with moving averages (MA20 / MA50 / MA200) to visualize short- vs. long-term momentum |
| **Sector Overview** | Treemap (squares) | Tickers grouped by sector, for a quick view of sector composition and weighting |
| **Volume analysis** | Bar chart | Daily trading volume over time, useful for spotting spikes in market activity |

## Data

The workbook connects to a single flat file: **`stock_prices_tableau_ready.csv`**

| Field | Type | Description |
|---|---|---|
| `Date` | Date | Trading day |
| `Ticker` | String | Stock symbol (120 tickers, e.g. AAPL, MSFT, JPM, XOM) |
| `Sector` | String | GICS-style sector classification |
| `Open`, `High`, `Low`, `Close` | Number | Daily OHLC prices |
| `Adj Close` | Number | Dividend/split-adjusted close |
| `Volume` | Number | Shares traded |
| `Ma20`, `Ma50`, `Ma200` | Number | 20/50/200-day simple moving averages |
| `Volatility 20d` | Number | Rolling 20-day volatility |
| `Volume MA20`, `Volume Ratio` | Number | Volume moving average and ratio vs. average |
| `Daily Return Pct` | Number | Day-over-day percent return |
| `Indexed Return Base100` | Number | Cumulative return indexed to 100 at the start date |
| `Trend Signal` | String | Derived trend label (e.g. bullish/bearish/neutral) |
| `Company Name`, `Month`, `Month Name`, `Quarter`, `Year` | — | Supporting dimensions for grouping and filtering |

> **Note:** The CSV data file is **not included** in this repo. To open the workbook, point the data connection to your own `stock_prices_tableau_ready.csv` with a matching schema, or export/replace the connection in Tableau (`Data > Edit Data Source`).

## Calculated Fields & Parameters

- **`Is Latest`** — Boolean calc (`[Date] = {FIXED : MAX([Date])}`) used to isolate the most recent trading day for leaderboard/summary views.
- **Selected Ticker (parameter)** — Lets users pick any of the 120 tickers to drive the Price Trend view; defaults to `AMZN`.

## Requirements

- **Tableau Desktop** (or Tableau Reader/Public) — workbook was built on the 2023.x file format (internal version `18.1`)
- A CSV data source matching the schema above

## Getting Started

1. Clone or download this repo.
2. Open `stocks_project.twb` in Tableau Desktop.
3. If prompted, reconnect the data source to your local copy of `stock_prices_tableau_ready.csv`.
4. Use the **Selected Ticker** parameter to explore individual stocks in the Price Trend view.

## Possible Extensions

- Add a dashboard that combines all four sheets with a global ticker/sector filter
- Add benchmark comparison (e.g., vs. S&P 500 index)
- Publish to Tableau Public for a live interactive version

## License

Feel free to fork and adapt for personal or educational use. Add a license file if you plan to distribute or accept contributions.
