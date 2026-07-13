# Market Timing vs Time in the Market

![Python](https://img.shields.io/badge/Python-3.11%2B-blue)
![Status](https://img.shields.io/badge/Status-Under%20Development-orange)
![Analysis](https://img.shields.io/badge/Analysis-Backtesting%20%26%20Risk-green)

This project compares different ways of investing **€50,000 over a 20-year horizon**.

Two capital availability scenarios are considered:

* **Upfront capital:** the full €50,000 is available on the first day.
* **Progressive capital:** an annual budget of €2,500 becomes available over time, for a total of €50,000 across 20 years.

The strategies compared are:

* **Lump Sum:** invest the full €50,000 on the first day and hold for 20 years.
* **Cash:** keep the full amount in cash for the entire period.
* **Annual Investing:** invest €2,500 once per year.
* **Monthly DCA:** invest approximately €208.33 every month.
* **Daily DCA:** divide the available budget across all trading days.
* **Buy the Dip:** accumulate cash and invest when the market falls by a predefined percentage from its previous peak.
* **Moving Average Strategy:** invest only when the market is above its long-term moving average, keeping contributions in cash otherwise.

Every strategy is evaluated using final portfolio value, total return, XIRR, volatility, maximum drawdown, Sharpe ratio, time spent in cash and cash drag.

The analysis is repeated across different rolling 20-year historical periods to test whether the results remain consistent across bull markets, crashes and long recoveries.

**Research question:**
*Is it better to invest immediately, invest gradually, wait for more favorable market conditions, or remain in cash?*

---

## Why This Project

Does market timing really deserve so much overthinking?

Investors often debate whether they should invest everything immediately, spread purchases over time, wait for a market correction, follow a trend signal or remain in cash. This project turns that debate into a reproducible quantitative experiment.

The objective is not to prove that one strategy is always superior. It is to measure how each approach behaves across different historical environments while controlling for capital availability, investment horizon and total contributed capital.

## Experimental Design

### Investment Horizon

Each backtest covers a complete **20-year period**.

### Capital Assumptions

The analysis separates two fundamentally different situations:

| Scenario | Capital availability | Total capital |
|---|---:|---:|
| Upfront capital | €50,000 available immediately | €50,000 |
| Progressive capital | €2,500 per year over 20 years | €50,000 |

This distinction prevents lump sum investing from being compared directly with periodic investing without acknowledging that the two strategies assume different access to capital.

### Rolling Windows

The strategies are tested across multiple rolling 20-year historical windows rather than one arbitrarily selected period.

This helps assess performance during different combinations of:

* bull markets
* bear markets
* recessions
* market crashes
* high and low inflation
* prolonged recoveries

## Strategy Definitions

### Lump Sum

The entire €50,000 is invested on the first available trading day and held for the full 20-year period.

### Cash

The full amount remains uninvested for the entire period. Depending on the selected configuration, cash may earn no return or a specified cash rate.

### Annual Investing

A yearly contribution of €2,500 is invested once per year.

### Monthly DCA

The yearly budget is divided into twelve equal contributions:

```text
€2,500 / 12 = approximately €208.33 per month
```

### Daily DCA

The available annual budget is distributed across all trading days of the year.

### Buy the Dip

Contributions accumulate in cash until the market reaches a predefined drawdown from its previous peak. Once the condition is met, the available cash is invested.

### Moving Average Strategy

Capital is invested only when the market price is above its selected long-term moving average. Contributions remain in cash whenever the signal is inactive.

## Performance Metrics

Each strategy is evaluated using:

| Metric | Purpose |
|---|---|
| Final portfolio value | Measures terminal wealth |
| Total return | Measures cumulative performance |
| XIRR | Accounts for the timing of individual cash flows |
| Annualized volatility | Measures return variability |
| Maximum drawdown | Measures the largest peak-to-trough loss |
| Sharpe ratio | Evaluates return relative to total volatility |
| Time spent in cash | Measures market participation |
| Cash drag | Estimates the opportunity cost of delayed investment |

Additional outputs may include median results, best and worst rolling periods, strategy rankings and the probability of outperforming the benchmark.

## Planned Visualizations

The analysis will include:

* portfolio value curves
* drawdown curves
* final value comparisons
* rolling 20-year return distributions
* strategy ranking heatmaps
* cash allocation over time
* cash drag comparisons
* risk and return scatter plots

## Repository Structure

```text
market-timing-analysis/
│
├── README.md
├── requirements.txt
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_strategy_backtests.ipynb
│   └── 03_rolling_window_analysis.ipynb
├── src/
│   ├── data_loader.py
│   ├── strategies.py
│   ├── backtester.py
│   ├── metrics.py
│   └── visualization.py
├── tests/
│   ├── test_strategies.py
│   └── test_metrics.py
└── outputs/
    ├── figures/
    └── tables/
```

## Methodological Principles

The project is designed around the following principles:

* equal total capital within each comparable scenario
* explicit capital availability assumptions
* reinvestment of distributions where supported by the dataset
* no look-ahead bias in rule-based strategies
* consistent trading calendars and execution dates
* transparent treatment of uninvested cash
* reproducible strategy parameters
* rolling-window analysis instead of cherry-picking one period

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/your-repository-name.git
cd your-repository-name
```

Create and activate a virtual environment:

```bash
python -m venv .venv
```

On Windows:

```bash
.venv\Scripts\activate
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

## Usage

Run the main analysis:

```bash
python main.py
```

Alternatively, open the notebooks in sequence:

```text
01_data_exploration.ipynb
02_strategy_backtests.ipynb
03_rolling_window_analysis.ipynb
```

Strategy parameters such as the drawdown threshold, moving average window, cash return and transaction costs can be configured before running the backtest.

## Roadmap

* Implement the core backtesting engine
* Add lump sum, cash and periodic investment strategies
* Add buy-the-dip and moving average strategies
* Calculate performance and risk metrics
* Introduce rolling 20-year analysis
* Add transaction costs, inflation and cash returns
* Create final charts and summary tables
* Add automated tests
* Publish the completed results

## Limitations

Historical performance does not guarantee future results. Outcomes depend on the selected market, data source, contribution timing, transaction assumptions, taxes, inflation and treatment of dividends.

The cash and lump sum strategies also represent different capital availability conditions from progressive contribution strategies. Results should therefore be interpreted within the appropriate scenario rather than as a perfectly identical comparison.

## Disclaimer

This project is for educational and research purposes only. It does not constitute financial advice or a recommendation to buy or sell any financial instrument.

## License

This project is released under the MIT License.
