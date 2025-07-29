# 🔑 Essential Concepts and Terms in Your Volatility Surface Project

### 🏦 Option
A financial contract giving the buyer the right (but not obligation) to buy or sell an asset at a fixed price in the future.

- Call option: Right to buy at strike price
- Put option: Right to sell at strike price
Options are priced based on how likely they are to end up profitable (called "in the money"), which depends on volatility, time to expiry, and the strike price.

### 📈 Strike Price (K)
The price at which the option lets you buy/sell the asset.

Example: A call option with strike 4000 on the S&P 500 means you can buy it at 4000, even if the market price is higher.
If the market is at 4100, the option is worth at least 100.

### ⏳ Maturity / Expiry (T)
How much time is left before the option expires.

Could be 7 days, 30 days, 90 days, etc.
As time passes, options lose value (this is called time decay)

### 💡 Volatility
A measure of how much an asset’s price is expected to move.

More volatility → more chance the option will be profitable → higher price
There are two types:

|Type	| Meaning|
-----------------
|Realised volatility | Historical, computed from past price movements|
----------
|Implied volatility |	Future volatility that is implied by the current market price of an option|
--

This project focuses on implied volatility.

### ❓ Implied Volatility (IV)
What the market thinks volatility will be, implied by the price of the option.

Calculated backwards from the Black-Scholes formula

If an option is expensive, it implies the market expects big movements (high IV)
This is what you will be computing at each (strike, maturity) pair.

### 🧮 Black-Scholes Model
A mathematical formula for the theoretical price of European options, given:

Strike 
K
K
Current price 
S
S
Time to maturity 
T
T
Volatility 
σ
σ
Interest rate 
r
r
But we flip it: we know the price, and solve backwards for implied volatility 
σ
σ.

### 🔄 Root-Finding Algorithm
A numerical method (like Newton-Raphson or Brent's method) to solve:

f
(
σ
)
=
Black-Scholes price
(
σ
)
−
Market price
=
0
f(σ)=Black-Scholes price(σ)−Market price=0
You iterate to find the volatility 
σ
σ that makes the theoretical price match the market price.

### 🧊 Volatility Smile / Skew
In theory, volatility should be constant for all strikes. But in reality, markets show:

Smile: Low and high strikes have higher implied vol
Skew: Implied vol varies with strike asymmetrically
Your surface will capture these effects.

### 🌄 Volatility Surface
A 3D surface showing implied volatility as a function of:
- Strike (K)
- Time to maturity (T)
You build this surface from raw option data, then smooth/interpolate it.

### 📐 Interpolation / Curve Fitting
You won’t have market data at every strike/maturity — so you fit a smooth surface over the data points.

Spline interpolation: Fit smooth curves between known points
Parametric models: Assume a mathematical form (like SVI or SABR)

### 🚫 No-Arbitrage Conditions
Arbitrage = risk-free profit — markets shouldn’t allow it.

There are known constraints your surface must satisfy to avoid impossible or exploitative pricing:

|Rule | What it means |
---
|Vertical spread |	Option price must decrease with strike |
--
|Butterfly spread	| Call price must be convex in strike (no dips in middle)|
-
|Calendar spread | Longer-dated options can’t be cheaper than shorter ones |
-

You’ll either check these after fitting, or include them as constraints during fitting.

### 📊 Backtest / Validation
You’ll use the surface to recompute option prices, and compare them with the original market prices.

If your fitted surface leads to similar prices, it’s accurate.
You can also plot:
- Smile curves (IV vs strike for fixed time)
- Term structure (IV vs maturity for fixed strike)
- 3D surface
