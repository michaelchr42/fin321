# Stage 4 – Final Analysis & Hedge Recommendation

**Prepared by:** Michael Christensen
**Date:** April 2, 2026
**Course:** FIN-321-002 | International Finance
**Institution:** University of Hawaiʻi at Mānoa, Shidler College of Business
**LLM Used:** Claude (Anthropic)

---

## A. Exposure Summary

&nbsp;&nbsp;&nbsp;&nbsp;TransLog Pacific LLC holds a confirmed EUR receivable of €2,500,000 from a European freight partner, due for settlement on July 31, 2026 — approximately 90 days from the analysis date. The payment is contractually fixed in euros and will be converted to USD upon receipt. At the current spot rate of 1.0820 USD/EUR, the implied USD value is approximately $2,705,000.

&nbsp;&nbsp;&nbsp;&nbsp;The risk is straightforward: if the euro depreciates against the dollar between now and settlement, realized USD proceeds will fall below budget. A 5% adverse move — well within historical EUR/USD volatility over a 90-day window — would reduce proceeds by approximately $135,000. A 10% move would cost over $270,000. For a logistics firm operating on thin margins, an unhedged FX loss of this magnitude is not an acceptable outcome. This analysis evaluates three hedging strategies and recommends the most appropriate course of action.

---

## B. Summary of Hedge Outcomes

&nbsp;&nbsp;&nbsp;&nbsp;All results below are derived from the Stage 2 Excel model at the baseline spot rate of 1.0820 USD/EUR and a 90-day settlement horizon.

**1. Forward Hedge — $2,699,500**
Lock in a rate of 1.0798 USD/EUR today, guaranteeing $2,699,500 in USD proceeds regardless of where the spot rate settles. Simple to execute, no upfront cost, and eliminates all FX uncertainty. The trade-off is that the firm forfeits any benefit if the euro strengthens — but for a firm prioritizing cash flow certainty, this is an acceptable cost.

**2. Money Market Hedge — ~$2,699,500**
Borrow the present value of €2,500,000 at the EUR rate (3.90%), convert to USD at spot, and invest at the USD rate (5.30%) for 90 days. The result is approximately equal to the forward hedge by covered interest parity, confirming the Stage 2 parity check. In practice, this approach is more operationally complex and consumes EUR borrowing capacity — making it less attractive than the forward for most corporate treasury teams unless derivative facilities are unavailable.

**3. EUR Put Option — Floor of ~$2,669,580**
Purchase a EUR put with strike K_PUT = 1.0800 at a premium of $0.0120/EUR. Total premium cost: $30,000 compounded to ~$30,397 at settlement. If EUR settles below 1.0800, the put is exercised and proceeds are floored at approximately $2,669,580. If EUR settles above 1.0800, the put expires worthless and the firm sells EUR at the higher market rate, retaining upside minus the premium cost. This strategy costs roughly $30,000 for meaningful downside protection while preserving participation in EUR appreciation.

**4. Call Option — Not Applicable**
A EUR call option hedges a payable exposure — it protects a USD-based buyer of euros against EUR appreciation. Since TransLog holds a receivable (long EUR), a call option would not reduce risk and is excluded from this analysis.

**5. No Hedge — Variable**
Unhedged proceeds equal S_T × €2,500,000. At the current spot of 1.0820, that is $2,705,000 — slightly above the forward. However, this exposes the firm to the full range of outcomes. At S_T = 1.0279 (−5%), proceeds fall to $2,569,750. At S_T = 1.1361 (+5%), proceeds rise to $2,840,250. The range is wide, and the downside is material.

---

## C. Sensitivity Interpretation

&nbsp;&nbsp;&nbsp;&nbsp;The Stage 2 sensitivity table models EUR/USD scenarios from 0.95 × S0 (1.0279) to 1.05 × S0 (1.1361), in 1% increments. Key observations:

**EUR depreciation scenarios (S_T < S0):** The forward and money market hedges outperform both the option and no-hedge positions. At S_T = 1.0279 (−5%), the forward delivers $2,699,500 while the unhedged position yields only $2,569,750 — a $129,750 advantage. The put option also provides protection, flooring proceeds near $2,669,580, but the premium cost means it underperforms the forward in all depreciation scenarios.

**EUR appreciation scenarios (S_T > S0):** The no-hedge position and the put option outperform the forward. At S_T = 1.1361 (+5%), the unhedged position yields $2,840,250 while the forward remains fixed at $2,699,500 — an opportunity cost of $140,750. The put option captures most of this upside (proceeds rise with S_T above the strike), minus the $30,397 compounded premium cost.

**Key crossover point:** The put option breaks even against the forward when EUR appreciation is sufficient to recover the premium — approximately when S_T exceeds 1.0920. Below that level, the forward produces higher net proceeds. Above it, the option's retained upside creates an advantage.

&nbsp;&nbsp;&nbsp;&nbsp;In summary: the forward wins in flat or depreciation scenarios; the option wins in strong appreciation scenarios; the no-hedge position has the widest range of outcomes with no downside protection.

---

## D. Strategic Recommendation

&nbsp;&nbsp;&nbsp;&nbsp;**Recommended strategy: Forward Hedge.**

&nbsp;&nbsp;&nbsp;&nbsp;For TransLog Pacific LLC, the forward contract is the optimal hedge. It eliminates FX uncertainty entirely at no upfront cost, locks in $2,699,500, and requires no ongoing management. Given that the firm's core business is logistics — not currency speculation — budget certainty outweighs the opportunity cost of forfeiting upside in an EUR appreciation scenario.

&nbsp;&nbsp;&nbsp;&nbsp;The put option is a credible alternative if management believes EUR appreciation is likely over the next 90 days, or if the firm wishes to preserve upside while still protecting the downside. At a premium cost of $30,000 (approximately 1.1% of notional), it is not prohibitively expensive — but it introduces premium outflow and operational complexity that the forward avoids entirely.

&nbsp;&nbsp;&nbsp;&nbsp;The money market hedge produces an equivalent financial result to the forward but is operationally heavier and uses EUR credit capacity that may be better deployed elsewhere. It is not recommended as a primary strategy given the availability of a forward contract.

---

## E. Executive Justification

**Cash flow certainty:** The forward contract converts a variable EUR receivable into a known, fixed USD cash flow of $2,699,500 on July 31, 2026. Finance and operations teams can plan and budget around a confirmed receipt with no residual FX variance — once the forward is in place, no further scenario planning is required.

**Liquidity impact:** The forward requires no upfront payment and creates no drag on operating liquidity. The put option, by contrast, requires $30,000 in premium outflow at inception — a real cash cost recovered only if EUR depreciates below the strike at settlement.

**Optionality value:** The put option's upside retention is genuinely valuable in EUR appreciation scenarios, but the 90-day horizon and current rate environment do not strongly favor EUR strength. ECB-Fed policy divergence may support a firmer USD over the near term, which would reduce the expected value of holding the option open. Under these conditions, paying $30,000 for optionality is difficult to justify.

**Premium costs:** At $0.0120/EUR on a €2,500,000 notional, the put premium is $30,000 — approximately 1.1% of notional. Compounded to settlement, the effective cost is ~$30,397. This is the price of optionality: reasonable in isolation, but unnecessary if management is comfortable locking in the forward rate.

**Conclusion:** Execute a 90-day EUR/USD forward contract to sell €2,500,000 at 1.0798 USD/EUR, settling July 31, 2026. Lock in $2,699,500 in USD proceeds with no upfront cost and no residual FX exposure.

---

## F. Structured AI Prompt

> The following prompt is written to instruct an AI assistant to reconstruct the Stage 2 FX hedge model from scratch. It is designed to be self-contained — no external files required.

---

```
# GOAL

Create a professional Excel workbook (.xlsx) modeling FX hedging strategies for a
USD-based firm holding a EUR receivable. The model should compare four positions —
Forward Hedge, Money Market Hedge, EUR Put Option, and No Hedge — and produce a
sensitivity table and line chart across a range of future spot rate scenarios.

---

# SCENARIO

Firm: TransLog Pacific LLC (U.S.-based logistics company)
Exposure: EUR receivable — contractually fixed, due in 90 days
Settlement Date: July 31, 2026
Analysis Date: April 2, 2026

---

# INPUT VARIABLES

Use the following values. Create a labeled Inputs section with all variables in
yellow-highlighted cells. Register each as a named range at the workbook level.

| Named Range | Description                        | Value     | Unit    |
|-------------|------------------------------------|-----------|---------|
| FC_AMT      | EUR receivable amount              | 2,500,000 | EUR     |
| S0          | Spot rate at inception (USD/EUR)   | 1.0820    | USD/EUR |
| F0          | 90-day forward rate (USD/EUR)      | 1.0798    | USD/EUR |
| R_USD       | U.S. interest rate (annualized)    | 0.0530    | Annual  |
| R_EUR       | EUR interest rate (annualized)     | 0.0390    | Annual  |
| T_DAYS      | Days to settlement                 | 90        | Days    |
| K_PUT       | EUR put strike price               | 1.0800    | USD/EUR |
| PREM_PUT    | EUR put premium per unit of EUR    | 0.0120    | USD/EUR |

No call option is required — this is a receivable exposure, not a payable.

---

# COLOR CODING CONVENTION

Apply consistently throughout the workbook:
- Yellow  (#FFFF00): All editable input cells
- Green   (#E2EFDA): All formula / intermediate calculation cells
- Gray    (#D9D9D9): All output / summary cells
- Blue    (#BDD7EE): Section headers and column label rows
- Dark blue (#1F3864 or #2F5496): Major section title bars (white bold text)

---

# MODEL LOGIC

Build the following sections in sequence on one sheet titled "FX Hedge Model":

## Section 1 — Inputs
List all 8 named range variables with labels, values, and units.
Yellow cells, named ranges registered at workbook level.

## Section 2 — Forward Hedge
Step [a]: USD proceeds = FC_AMT × F0
Output: single USD value. Label clearly as locked-in proceeds.

## Section 3 — Money Market Hedge
Step [a]: Borrow PV of EUR receivable = FC_AMT / (1 + R_EUR × T_DAYS/360)
Step [b]: Convert to USD at spot = result of [a] × S0
Step [c]: Invest USD = result of [b] × (1 + R_USD × T_DAYS/360)
Step [d]: EUR receivable repays EUR loan exactly — nets to zero.
Output: result of step [c] as USD proceeds.
Add a parity check row: Forward minus MM result (should be approximately $0).

## Section 4 — Option Hedge (EUR Put)
Step [a]: Premium outflow today = −PREM_PUT × FC_AMT (negative, USD)
Step [b]: FV of premium at settlement = result of [a] × (1 + R_USD × T_DAYS/360)
Step [c]: Floor proceeds = K_PUT × FC_AMT + result of [b]
At any future spot S_T: Proceeds = MAX(K_PUT, S_T) × FC_AMT + result of [b]
Output: floor USD proceeds (worst-case).

## Section 5 — Summary Output
Table with one row per strategy:
- Row 0: No Hedge — S0 × FC_AMT (indicative only; variable at settlement)
- Row 1: Forward Hedge — from Section 2
- Row 2: Money Market Hedge — from Section 3
- Row 3: Option Hedge (floor) — from Section 4
- Row 4: RECOMMENDATION — Forward Hedge; execute 90-day forward to sell
  €2,500,000 at 1.0798 USD/EUR, settling July 31, 2026.
Columns: Strategy | USD Proceeds | Certainty | Key Trade-off

## Section 6 — Sensitivity Table
Vary future spot rate S_T from 0.95 × S0 to 1.05 × S0 in 11 steps of 1%.
For each S_T, compute:
- Column B: S_T value (= S0 × (1 + pct), yellow)
- Column C: % vs. spot (= S_T / S0 − 1, green)
- Column D: No Hedge proceeds (= S_T × FC_AMT)
- Column E: Forward proceeds (= fixed output from Section 2)
- Column F: Money Market proceeds (= fixed output from Section 3)
- Column G: Option proceeds (= MAX(K_PUT, S_T) × FC_AMT + FV_premium)
- Columns H–J: Each hedge minus No Hedge (P&L vs. unhedged)
- Column K: Best Hedge label (IF formula comparing D, E, F, G)
- Column L: Notes for −5%, 0%, and +5% rows

---

# VERIFICATION CHECKS

1. Forward vs. MM parity: Section 3 parity check row should show a difference
   near $0 (within $500 is acceptable given Actual/360 rounding).
2. Option floor: Section 4 floor proceeds should equal K_PUT × FC_AMT + FV_premium.
3. Sensitivity logic: Option proceeds in Column G should equal forward proceeds
   at S_T = K_PUT, and diverge upward above the strike.
4. Best Hedge column: Should show "Forward" or "Money Mkt" for all depreciation
   scenarios, and "Option" for strong appreciation scenarios.

---

# ADDITIONAL REQUIREMENTS

- Freeze panes at row 3 so the title remains visible when scrolling.
- Add a second sheet titled "Notes & Assumptions" with a two-column table
  documenting: spot rate source, forward rate derivation (CIP), day count basis
  (Actual/360), bid-ask exclusion, option style (European), MM credit assumption,
  and model author (Michael Christensen, FIN-321-002, UH Mānoa).
- Add a line chart below the sensitivity table showing USD proceeds (Y-axis) vs.
  future spot rate (X-axis) for all four strategies. Title: "USD Proceeds Across
  EUR/USD Settlement Scenarios."
- File name: christensen-michael-stage2-model.xlsx

---

# EXPORT

Save as .xlsx. Confirm: 0 formula errors, named ranges registered, color coding
applied, Notes tab complete, chart present.
```

---

## Extra Credit — Areas for Further Study

**1. AI Skills & Automation**

&nbsp;&nbsp;&nbsp;&nbsp;The workflow used in this project — spec → model → prompt — is a manual approximation of what AI automation tools can do end-to-end with live data. A more advanced implementation would use an AI agent with access to a market data API (Bloomberg, Refinitiv, or even a free source like FRED) to pull live EUR/USD spot rates, SOFR, and Euribor at the start of each session and automatically populate the named range inputs before running the model. Claude's tool-use and code execution capabilities could regenerate the full sensitivity table on demand — for example, triggered each morning — without any analyst intervention. Monte Carlo simulation is a natural extension: instead of a fixed ±5% range, the model would draw thousands of S_T scenarios from a calibrated distribution using historical EUR/USD realized volatility (currently around 6–8% annualized) and output a probability-weighted distribution of USD proceeds under each strategy. This would let the CFO see not just the range of outcomes but their relative likelihood — a substantially more rigorous basis for a hedging decision.

**2. GitHub & Version Control**

&nbsp;&nbsp;&nbsp;&nbsp;Committing each stage of this project to a GitHub repository does more than satisfy the assignment requirements — it creates an auditable, reproducible record of the entire analytical process. In a professional setting, this matters significantly. Regulators, auditors, and internal risk committees increasingly expect financial models to be version-controlled: who built it, when, what changed between versions, and what inputs were used at the time a hedge was executed. A GitHub repository containing the Stage 1 memo, Stage 2 model, Stage 3 specification, and Stage 4 prompt effectively constitutes a hedge documentation file — the kind of artifact required under ASC 815 for hedge accounting designation. If the forward rate or premium assumption changes between analysis and execution, a new commit captures that update with a timestamp and a commit message explaining the revision. This is a meaningful improvement over the standard practice of saving `model_v3_FINAL_revised2.xlsx` to a shared drive. As AI-generated models become more common in finance, version-controlled repositories will likely become the expected standard for model governance and audit readiness.

**3. Multi-File Reasoning**

&nbsp;&nbsp;&nbsp;&nbsp;One of the most practical near-term applications of AI in financial modeling is multi-file reasoning: giving an AI assistant simultaneous access to the spec, the model, and the prompt, and asking it to verify consistency across all three. In this project, an AI with access to all four stage files could check that every named range in the Stage 3 spec appears correctly in the Stage 2 model, that the Stage 4 prompt uses the same variable values as the Stage 2 inputs, and that the sensitivity range in the chart matches what the spec describes. Discrepancies — a mismatched interest rate, a renamed variable, a formula that doesn't match the spec's described logic — would be flagged automatically. This kind of cross-file consistency check is tedious and error-prone when done manually, and it is exactly the type of structured reasoning task that current AI models handle well. As model complexity grows — multi-currency exposures, rolling hedge programs, dynamic rebalancing — multi-file AI reasoning becomes not just useful but necessary for maintaining model integrity.

---

*Prepared by: Michael Christensen | FIN-321-002 | International Finance | University of Hawaiʻi at Mānoa, Shidler College of Business*
