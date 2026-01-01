# Quantitative Stock Analyst

This project implements an automated daily stock analysis pipeline using Python. It combines technical indicators (Moving Averages, RSI, MACD) with Hidden Markov Models (HMM) to identify market regimes and generate trading signals.

## Features

- **Multi-Factor Analysis**: Combines MA10, MA50, RSI, MACD, and HMM Market States.
- **Hidden Markov Models**: Uses Gaussian HMM to classify market regimes (Bear, Neutral, Bull) based on Log Returns and Range Volatility.
- **Smart Scheduling**: Automatically checks for valid NYSE trading days and runs only after market close (16:15 ET).
- **Historical Data Tracking**: Appends daily analysis snapshots to `history_data.csv` to build a long-term dataset.
- **Automated Execution**: Configured with GitHub Actions to run daily at 21:30 UTC (4:30 PM EST).

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/bradchang-ux/quantitative-analyst.git
   cd quantitative-analyst
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the analysis script directly:

```bash
python "Quantitative analyst.py"
```

The script will:
1. Check if the market is currently closed and if today is a trading day.
2. Download data for the configured tickers (MSFT, AAPL, NVDA, etc.).
3. Perform HMM and Technical Analysis.
4. Print a dashboard summary for each ticker.
5. Save the results to `history_data.csv`.

### Configuration

You can modify the `Config` class in `Quantitative analyst.py` to change:
- `TICKERS`: List of stocks to analyze.
- Strategy parameters (MA windows, RSI thresholds, HMM components).

## Automation

The project includes a GitHub Actions workflow (`.github/workflows/daily_analysis.yml`) that:
- Runs every weekday at 21:30 UTC.
- Executes the analysis script.
- Commits the updated `history_data.csv` back to the repository.

## Dislcaimer

This software is for educational purposes only. Do not trade based solely on these signals.
