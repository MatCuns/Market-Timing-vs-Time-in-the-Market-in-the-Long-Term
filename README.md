![Python](https://img.shields.io/badge/Python-3.11%2B-blue)
![Status](https://img.shields.io/badge/Status-Under%20Development-orange)

# Market Timing vs Time in the Market in the Long Term

This project compares different ways of investing **€50,000 over a 20 year horizon** and never selling.

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
* **Buying at All Time High:** invest the full yearly amount at the highest peak of the same year (forward looking and taken as the "worst scenario")
* **Moving Average Strategy:** invest only when the market is above its long term moving average, keeping contributions in cash otherwise.

Every strategy is evaluated using final portfolio value, total return, XIRR, volatility, maximum drawdown, Sharpe ratio, time spent in cash and cash drag.

**Research question:**


## Why This Project

Does market timing really deserve so much overthinking?

Investors often debate if it is better to invest immediately, invest gradually, wait for more favorable market conditions, or remain in cash. This project turns that debate into a reproducible quantitative experiment.

The objective is not to prove that one strategy is always superior. It is to measure how each approach behaves over the long term while controlling for capital availability, investment horizon and total contributed capital.
