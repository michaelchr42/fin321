# FX Receivable Hedge Model – Technical Specification

**Created by:** Michael Christensen
**Updated by:** Michael Christensen
**Date Created:** April 2, 2026
**Date Updated:** April 2, 2026
**Version:** 1.0
**LLM Used:** Claude (Anthropic)

**Role:** Treasury Analyst
**Audience:** CFO / Director of Treasury

**Purpose:** Document the analytical structure of the Stage 2 EUR/USD receivable hedge model, identify its limitations, and provide a refined specification sufficient for a treasury analyst or AI assistant to reconstruct and improve the model from scratch.

---

## 1. Problem Statement

&nbsp;&nbsp;&nbsp;&nbsp;TransLog Pacific LLC expects to receive a contractually fixed payment of €2,500,000 from a European freight partner, settling on July 31, 2026 — approximately 90 days from the analysis date of April 2, 2026. The payment is denominated in EUR and will be converted to USD upon receipt. At the current spot rate of 1.0820 USD/EUR, the implied USD value is approximately $2,705,000. However, this amount is not guaranteed: if the euro depreciates against the dollar before settlement, realized USD proceeds will fall short of projections.

&nbsp;&nbsp;&nbsp;&nbsp;This specification documents the analytical framework used to quantify, compare, and evaluate three hedging strategies — a forward contract, a money market hedge, and a EUR put option — against an unhedged baseline. The objective is to protect the USD value of the receivable while clearly communicating the trade-offs of each approach to senior management.

---

## 2. Inputs (Known Variables)

| Named Range | Description | Unit | Value | Source |
|---|---|---|---|---|
| `FC_AMT` | EUR receivable amount | EUR | 2,500,000 | Contract |
| `S0` | Spot rate at inception | USD/EUR | 1.0820 | Market data, Apr 2026 |
| `F0` | 90-day outright forward rate | USD/EUR | 1.0798 | Derived via CIP |
| `R_USD` | U.S. interest rate (annualized) | Annual % | 5.30% | 90-day SOFR / T-bill proxy |
| `R_EUR` | EUR interest rate (annualized) | Annual % | 3.90% | 90-day Euribor proxy |
| `T_DAYS` | Days to settlement | Days | 90 | Contract |
| `K_PUT` | EUR put strike price | USD/EUR | 1.0800 | Analyst choice (at-the-money) |
| `PREM_PUT` | EUR put premium per unit | USD/EUR | 0.0120 | Market estimate |

&nbsp;&nbsp;&nbsp;&nbsp;No call option is included in this model, as the firm holds a receivable (long EUR exposure) and has no need to hedge upside participation via a call. A call would be relevant for a payable scenario.

---

## 3. Assumptions & Constraints

- Interest rates are quoted on a simple annual basis and accrued using an **Actual/360** day count convention for both USD and EUR.
- The forward rate F0 is treated as an exogenous market input but is also consistent with covered interest parity: F0 ≈ S0 × (1 + R_USD × T_DAYS/360) / (1 + R_EUR × T_DAYS/360).
- Bid-ask spreads are excluded; all rates represent mid-market levels.
- Transaction costs and credit costs are not modeled.
- The EUR put option is **European-style**: exercisable at expiry only.
- The put premium is paid upfront in USD and compounded to settlement date at R_USD for comparability.
- The money market hedge assumes the firm has access to a EUR credit facility at the quoted R_EUR rate.
- All exchange rates are expressed as USD per EUR (direct quotation from a U.S. firm's perspective).

---

## 4. Calculation Flow

**Forward Hedge**

Multiply FC_AMT by F0 to compute locked-in USD proceeds. This result is fixed regardless of where the spot rate settles on July 31. No further steps are required.

**Money Market Hedge**

1. Borrow the present value of FC_AMT in EUR today: divide FC_AMT by (1 + R_EUR × T_DAYS/360). This is the amount borrowed.
2. Convert the borrowed EUR to USD at the current spot rate S0.
3. Invest the resulting USD at R_USD for T_DAYS/360 years. The future value of this investment is the locked-in USD proceeds.
4. At settlement, receive FC_AMT from the counterparty and use it to repay the EUR loan in full. The EUR leg nets to zero.

&nbsp;&nbsp;&nbsp;&nbsp;The money market result should approximate the forward hedge result by covered interest parity. Any residual difference is attributable to Actual/360 rounding and should be disclosed.

**Option Hedge (EUR Put)**

1. Compute total premium outflow: multiply PREM_PUT by FC_AMT (negative, as it is a cost).
2. Compound the premium to settlement date: multiply by (1 + R_USD × T_DAYS/360) to express the cost in future-value terms.
3. At settlement, if the spot rate S_T is below K_PUT, exercise the put and sell EUR at K_PUT. If S_T is above K_PUT, sell EUR at the prevailing spot rate S_T.
4. Net USD proceeds = MAX(K_PUT, S_T) × FC_AMT + FV of premium cost.

**Unhedged Baseline**

USD proceeds = S_T × FC_AMT. Entirely dependent on the settlement spot rate; no floor, no ceiling.

---

## 5. Outputs

| Output | Description | Format |
|---|---|---|
| `USD_forward` | Locked-in USD proceeds via forward contract | Single value |
| `USD_mm` | USD proceeds via money market hedge | Single value |
| `USD_mm_parity` | Forward minus MM result (parity check) | Single value, should ≈ $0 |
| `USD_option_floor` | Floor USD proceeds if put is exercised | Single value |
| `Sensitivity Table` | USD proceeds for all four strategies across 11 spot scenarios (S0 × 0.95 to S0 × 1.05, 1% steps) | Table |
| `Hedge P&L Table` | Each hedge's proceeds minus the unhedged baseline at each scenario | Table |
| `Best Hedge Column` | Strategy producing the highest USD proceeds at each scenario | Text column |
| `Chart_1` | Line chart of all four strategies vs. future spot rate | Line chart |
| `Summary Section` | Side-by-side strategy comparison with certainty rating and trade-off notes | Table with TBD recommendation row (Stage 4) |

---

## 6. Model Review — What Worked & What to Improve

**What worked correctly:**

- All three hedge calculations produce internally consistent results. The forward and money market outputs are within rounding of each other, confirming covered interest parity holds under the Actual/360 convention.
- Named ranges (FC_AMT, S0, F0, etc.) are registered at the workbook level, making the model fully dynamic — any input change propagates instantly to all outputs and the sensitivity table.
- Color coding (yellow inputs, green formulas, gray outputs) is consistently applied and legible.
- The sensitivity table and chart correctly visualize the asymmetric payoff profile of the option hedge relative to the linear hedges.

**What should be improved in a rigorous version:**

- **T_DAYS input:** The model currently uses T_DAYS as a fixed integer. A more robust version would derive T_DAYS automatically from a settlement date input using a date-difference formula, eliminating manual update risk.
- **Forward rate derivation:** F0 is entered as a hardcoded input. It should be computed endogenously from S0, R_USD, R_EUR, and T_DAYS via the CIP formula, with the hardcoded value available as an override for cases where a market quote differs from the theoretical rate.
- **Option premium:** PREM_PUT is a flat market estimate. An improved version would include a Black-Scholes approximation cell using implied volatility as an additional input, giving the analyst a sanity-check on the quoted premium.
- **No-hedge row in sensitivity:** The current "Best Hedge" column compares only the three hedges against each other. It should also flag when no hedge outperforms all three, which can occur in strongly appreciating EUR scenarios with low option premium costs.
- **Layout:** The six sections are stacked vertically on a single sheet. Splitting inputs onto a dedicated "Inputs" tab and keeping the main sheet for calculations and outputs would improve auditability.

---

## 7. Sensitivity Plan

&nbsp;&nbsp;&nbsp;&nbsp;The sensitivity table varies the future EUR/USD spot rate S_T from 0.95 × S0 to 1.05 × S0 in increments of 1%, producing 11 scenarios. At each scenario, USD proceeds are computed for all four strategies (unhedged, forward, money market, option). A separate P&L column shows each hedge's proceeds minus the unhedged baseline, making the cost or benefit of hedging immediately visible.

&nbsp;&nbsp;&nbsp;&nbsp;The ±5% range is chosen to reflect realistic short-term EUR/USD volatility over a 90-day horizon, consistent with historical one-standard-deviation moves. The most analytically useful comparisons are: (1) forward vs. unhedged, which shows the cost of certainty in appreciating EUR scenarios; and (2) option vs. unhedged, which shows the premium paid for downside protection while retaining upside. The crossover point — where the option outperforms the forward — occurs when EUR appreciates enough that the premium cost is recovered through higher spot proceeds.

---

## 8. Limitations & Next Steps

&nbsp;&nbsp;&nbsp;&nbsp;This model does not incorporate implied volatility, dynamic hedging, credit or counterparty risk, accounting treatment (ASC 815 / hedge designation), or bid-ask execution costs. The option premium is a flat market estimate rather than a model-derived price. The sensitivity range is fixed and does not represent a probability-weighted distribution of outcomes.

&nbsp;&nbsp;&nbsp;&nbsp;This specification feeds directly into Stage 4, where the calculation flow, named ranges, and improvement notes above will serve as the structured input to an AI prompt. The AI will be asked to reconstruct the improved model — incorporating endogenous forward rate derivation, date-based T_DAYS, and a split-tab layout — and to produce a final hedge recommendation with supporting quantitative rationale.

---

*Prepared by: Michael Christensen | FIN-321-002 | International Finance | University of Hawaiʻi at Mānoa, Shidler College of Business*
