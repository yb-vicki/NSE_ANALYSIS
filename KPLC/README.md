# Empirical Factor Research: Foreign Investor Flow Momentum on the NSE (KPLC)

A quantitative analysis research project analyzing whether daily institutional order flow from offshore investors on the Nairobi Securities Exchange (NSE) contains predictive alpha for **Kenya Power & Lighting Co. (KPLC)** across **2,319 trading sessions (2017–2026)**.

---

## Key Empirical Findings

1. **Failure of Naive Day-Trading Hypotheses:**
   * Same-day returns on foreign inflow days (+0.28%) vs. outflow days (+0.05%) show no statistical significance via a two-sample Welch's $t$-test ($p = 0.225$). Same-day price impact is dominated by local market noise.
2. **Order Flow Persistence (Autocorrelation):**
   * Institutional net foreign flows exhibit significant positive autocorrelation ($r = +0.244$ at Lag 1), remaining statistically significant out to Lag 10. Large offshore desks work block parent orders over 1–2 weeks due to liquidity constraints.
3. **Information Coefficient (IC) Decay:**
   * Predictive capacity peaks over medium horizons. Trailing 10-day foreign flow predicts 20-day forward returns with a **Spearman Rank Information Coefficient of +0.144**.
4. **Monotonic Quantile Spread:**
   * A 5-quantile portfolio sort confirms strict monotonicity:
     * **Q1 (Heavy Foreign Selling):** -1.12% mean 20-day forward return (Win Rate: 34.3%).
     * **Q5 (Heavy Foreign Buying):** +4.48% mean 20-day forward return (Win Rate: 47.4%).
     * **Q5 - Q1 Spread:** +5.60% forward return spread per 20-day cycle.
5. **Frontier Market Friction & Hysteresis:**
   * Standard sign-based switching rules suffer catastrophic fee erosion from NSE statutory costs (~2.0% round-trip).
   * Implementing an asymmetric hysteresis state machine ($Z$-score / threshold deadbands) suppresses trade churn, cutting maximum drawdowns from -89.4% down to -52.6% on a gross basis.

---

## Institutional Scorecard (2017 – 2026)

| Metric | Buy & Hold (KPLC) | Flow Strategy (Gross) | Flow Strategy (Net of 1.0% Fee) |
| :--- | :---: | :---: | :---: |
| **Total Return** | 112.27% | **217.49%** | 19.41% |
| **CAGR** | 8.52% | **13.38%** | 1.95% |
| **Annual Volatility** | 42.42% | **26.69%** | 27.01% |
| **Sharpe Ratio ($R_f = 9\%$)** | -0.01 | **0.16** | -0.26 |
| **Sortino Ratio** | -0.02 | **0.14** | -0.24 |
| **Max Drawdown** | -89.36% | **-52.61%** | -74.87% |
| **Calmar Ratio** | 0.10 | **0.25** | 0.03 |

---

## Repository Structure

* `01_data_cleaning_and_validation.ipynb`: Ingestion pipeline handling delimiter bleed, non-trading calendar filtering, and single-session bad prints.
* `02_eda_and_empirical_facts.ipynb`: Microstructure distributions, Welch's $t$-test, ACF autocorrelation decay, and 5-quantile monotonicity evaluation.
* `03_signal_generation_and_backtesting.ipynb`: Lookahead-free execution ($t+1$), asymmetric hysteresis state-machine, and cost-aware transaction modeling.
EOF
