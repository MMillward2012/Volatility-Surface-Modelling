# Volatility-Surface-Modelling
This project models implied volatility surfaces from European option prices, using parametric fitting techniques (e.g. SVI and SABR) under the Black-Scholes framework.
Core components:
- Implied volatility calculation via numerical inversion (e.g. Brent’s method)
- Arbitrage checks and constraint enforcement (butterfly spread convexity, calendar monotonicity)
- Surface fitting with parameter optimisation (least-squares error minimisation)
- Visualisation of vol smiles and surfaces across maturities and strikes
