# Volatility Surface Modelling

This project constructs an implied volatility surface using real-world options data, allowing visualisation and analysis of market volatility smiles, skews, and term structures. The aim is to develop a robust, arbitrage-aware surface fitting pipeline with potential extensions into more advanced quantitative finance methods.

## 📈 Overview

- ✅ Extract implied volatilities from market data using Black-Scholes inversion
- ✅ Fit a smooth surface to implied volatility across strikes and maturities
- ✅ Visualise the volatility surface and identify features like smiles and skews
- ✅ Validate against market prices and optionally enforce arbitrage constraints

---

## ⚙️ Features

### 1. Data Pipeline
- Sources historical options data (e.g. for the S&P 500 or a liquid ETF like SPY)
- Cleans and filters by moneyness, time-to-maturity, and liquidity

### 2. Implied Volatility Calculation
- Inverts the Black-Scholes formula to compute implied volatility from observed option prices
- Handles both call and put options using put-call parity as needed
- Vectorised for efficient batch computation

### 3. Surface Fitting
- Interpolates implied volatilities over a 2D grid (strike × maturity)
- Default: Bicubic spline or radial basis interpolation
- Includes basic arbitrage checks (e.g. monotonicity in time, convexity in strike)

### 4. Visualisation
- Plots:
  - 2D slices (volatility smile at different maturities)
  - 3D surface of implied volatilities
- Highlights mispricings, anomalies, and local structure

---

## 🧠 Extensions (Future Work)

These are not required for a working model but can significantly enhance the sophistication and realism of the project:

### 🔹 SVI Surface Fitting
Fit the implied volatility surface using the Stochastic Volatility Inspired (SVI) parametrisation with no-arbitrage constraints. Widely used in industry.

### 🔹 SABR Model Calibration
Apply the SABR stochastic volatility model to fit implied vols across maturities. Useful for FX or interest rate options.

### 🔹 Dupire Local Volatility Surface
From the implied surface, compute the local volatility surface using Dupire’s formula and finite differences.

### 🔹 Neural Network Surface
Train a neural network to predict implied volatility from strike and maturity. Compare interpolation/generalisation quality to splines and SVI.

### 🔹 Arbitrage-Free Interpolation
Use constrained optimisation to enforce:
- Convexity in strike
- Monotonicity in maturity
- No butterfly or calendar spread arbitrage

---

## 🛠 Tech Stack

- **Python**: Core implementation
- **NumPy / Pandas**: Data handling
- **SciPy**: Optimisation and interpolation
- **Matplotlib / Plotly**: Visualisation
- **yfinance / Nasdaq API**: Data acquisition (optional)

---

## 📚 Background

This project is inspired by practical needs in options pricing and risk management. Accurately modelling implied volatility surfaces is central to:

- Exotic option pricing
- Hedging strategies
- Market-making
- Volatility arbitrage

While the initial version focuses on static surface fitting, further extensions aim to align with real-world quantitative trading applications.

---

## ✅ Status

- [ ] Data retrieval & cleaning
- [ ] Implied volatility extraction
- [ ] Surface fitting & plotting
- [ ] Arbitrage checks
- [ ] SVI surface (planned)
- [ ] Dupire local vol (planned)

---

## 📌 Author

Matthew Millward  
Feel free to explore my portfolio or reach out with feedback or questions.
