# G-Research Quant Challenge @ ETH Zurich
This repository contains my algorithm for the G-Research Cointegration Challenge held at ETH Zurich in October 2024. The objective of the challenge was to develop a profitable trading strategy based on pairs trading—a market-neutral approach where two assets are selected based on their historical relationship and traded to exploit deviations in their prices.

## Strategy Overview

### Pairs Trading in General
The strategy is a form of a statistical arbitrage. It involves pairing assets and performing OLS regression of one asset’s price against the other. The residuals from this regression are then analyzed for stationarity using the ADF test. If the spread residuals are found to be stationary, it indicates that any deviation from the mean spread is temporary and will revert to zero over time. When a sufficient mismatch occurs between the paired asset prices, the strategy capitalizes on this opportunity by simultaneously going long the undervalued asset and shorting the overvalued asset. Positions are exited once the expected mean reversion has occured, i.e. this mean-reversion approach secures a profit when the prices converge back to their expected relationship.

### Pairs Selection
The strategy focused on identifying asset pairs with the strongest indication of cointegration, ensuring a high likelihood that any price divergence would eventually revert to the mean. Using statistical analysis, I ranked asset pairs by their cointegration certainty, selecting those with the most stable, consistent relationships.

### Trading Execution
Once a cointegrated pair was chosen, the strategy monitored for price divergence. When one asset's price moved sufficiently away from its historical relation with the other, trades were initiated to capture profit upon mean-reversion. Positions were closed once prices converged back to the expected spread.

## Repository Structure
- **`Cointegration Challenge.ipynb`**: Main notebook that contains the skeleton code, trading scripts for pairs selection, cointegration testing, and mean-reversion monitoring.
- **`README.md`**: Overview of the challenge.
