# DECISION MEMO

**TO:** Chief Financial Officer  
**FROM:** Michael Christensen, Finance  
**DATE:** April 3, 2026  
**RE:** EUR Receivable Exposure & Hedging Consideration  
**CLASSIFICATION:** Internal/Confidential  

---

## Situation

&nbsp;&nbsp;&nbsp;&nbsp;Our European logistics operations have a confirmed receivable of €2,500,000, expected to settle on July 31, 2026, roughly 90 days from today. The payment is fixed in euros and will be converted to USD upon receipt. At the current spot rate of approximately 1.0820 USD/EUR, that comes out to about $2,705,000 in USD proceeds.

&nbsp;&nbsp;&nbsp;&nbsp;The problem: that number isn't locked in.

---

## The Risk

&nbsp;&nbsp;&nbsp;&nbsp;The core issue is exchange rate volatility. Between now and settlement, EUR/USD could move in either direction, but only one direction hurts us. If the euro weakens against the dollar before we collect, our USD proceeds come in below plan.

&nbsp;&nbsp;&nbsp;&nbsp;To put numbers to it: a 5% drop in EUR/USD (to ~1.028) would cost us roughly $135,000. A 10% move—well within normal EUR/USD volatility over a 90-day window—would cost over $270,000. These aren't tail-risk scenarios; Fed/ECB policy divergence alone has driven moves this size in recent years. We shouldn't leave this exposure unmanaged.

---

## Strategies Under Consideration

1. Forward Contract  
   Lock in a fixed USD/EUR rate today for delivery on July 31.  
   - Pro: Removes all uncertainty; simple to execute; no upfront cost.  
   - Con: Gives up any upside if EUR strengthens; locks us into an obligation.

2. FX Options (Purchased Put on EUR)  
   Buy the right, not the obligation, to sell EUR at a set rate on or before settlement.  
   - Pro: Limits downside while keeping upside open; flexible.  
   - Con: Requires an upfront premium (est. 1–2% of notional); slightly more complex.

3. Money Market Hedge  
   Borrow EUR now, convert to USD at spot, invest the proceeds, and repay the loan with the receivable.  
   - Pro: Works without derivatives; useful if we lack hedging facilities.  
   - Con: Needs EUR credit access; uses borrowing capacity; more moving parts.

---

## Next Steps

&nbsp;&nbsp;&nbsp;&nbsp;This memo is the first of a four-stage analysis:

- **Stage One: Executive Memo**
  - Outline the FX exposure, identify the risk, and introduce the hedging strategies under consideration. (This document.)
- **Stage Two: Excel Model**
  - Build a working model comparing hedge outcomes (forward, option, unhedged) across a range of possible settlement rates, with P&L impact for our €2.5M exposure.
- **Stage Three: Technical Specification**
  - Document the model and design an improved version with clear formula definitions, scenario parameters, and sensitivity tables.
- **Stage Four: Final Recommendation**
  - Choose a hedge strategy based on the model results, draft a supporting AI prompt, and present the final case to CFO.

---

*Prepared by: Michael Christensen | FIN-321-002 | International Finance | University of Hawaiʻi at Mānoa, Shidler College of Business*
