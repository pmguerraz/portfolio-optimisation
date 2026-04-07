# Multi-Asset Portfolio Optimisation & Risk Management

Python notebook exploring Modern portfolio theory, different optimisation frameworks, forward-looking risk estimation (Monte Carlo Simulation, VaR/CvaR), and backtesting across four asset classes.



## Key Methods

- **Portfolio Optimisation:** all optimisations use `scipy.optimize.minimize`, long-only constraints (weights ∈ [0, 1]), and a budget constraint (weights sum to 1)
- **GMVP:** minimises portfolio variance with no return target
- **Tangency Portfolio:** maximises the Sharpe ratio, lies at the point of tangency between the Capital Allocation Line and the efficient frontier
- **Min-Variance with Target Return:** adds a second equality constraint fixing expected return to a specified level
- **Mean-Variance Utility:** maximises `U = μ − ½Aσ²`, where `A` is the investor's risk aversion coefficient
- **Monte Carlo simulation:** 10,000 correlated daily return paths via Cholesky decomposition of the covariance matrix, projected over a 1-year horizon
- **Historical VaR / CVaR:** empirical percentiles of the daily return distribution
- **Parametric VaR / CVaR:** closed-form normal distribution estimates
- **Monte Carlo VaR / CVaR:** simulated 1-day return distribution



## Notes

- The risk-free rate is set to 4% per annum (`RF = 0.04`) throughout
- All optimisations assume long-only positions (no short selling)
- Annualised figures use 252 trading days per year
- The 5,000 randomly generated portfolios (Dirichlet-sampled) are used for visualisation only, all optimal portfolios are found analytically via scipy
- All VaR metrics are computed at both 95% and 99% confidence levels across four portfolios
- The backtest uses realised historical returns and does not account for transaction costs, slippage, or rebalancing



## Dependencies

```
numpy
pandas
yfinance
matplotlib
seaborn
scipy
```

Install with:

```bash
pip install numpy pandas yfinance matplotlib seaborn scipy
```