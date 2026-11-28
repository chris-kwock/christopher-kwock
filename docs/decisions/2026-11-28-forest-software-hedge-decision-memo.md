# Memorandum — EUR Receivable Hedge Decision

**To:** Chief Financial Officer, Forest Software  
**From:** Christopher Kwock  
**Date:** November 28, 2026  
**Subject:** Recommended hedge for Finnish customer receivable  
**Status:** Conditional recommendation; numerical production test complete; executable quotes pending

## A. Exposure summary

Our company expects to receive EUR 1.7 million from a Finnish timber customer in 182 days. Because our operating expenses and investment needs are primarily denominated in U.S. dollars, a decline in the euro could reduce the cash available to meet these obligations. At the November 20 reference exchange rate of 1.0990 USD/EUR, the receivable is worth $1,868,300. The primary objective is to protect this cash flow and establish a reliable budget rather than speculate on the direction of the euro. The analysis assumes full and timely payment by the customer and a hedge covering the entire receivable.

## B. Hedge outcomes

The assigned forward rate of 1.1705 would lock in $1,989,850 before fees, regardless of the exchange rate at settlement. This is the highest modeled outcome among the receivable strategies across the tested range of exchange rates. However, the quote was supplied with the original scenario and has not been confirmed as executable on the market-data date. Its attractiveness must therefore be evaluated separately from the merits of using a forward contract.

The money-market hedge provides approximately $1,878,869 in fixed proceeds using the November 20 benchmark rates. It achieves the same economic objective as the forward by borrowing euros, converting the proceeds into dollars and investing them until the receivable is collected. Unlike a forward, it requires a borrowing facility and an investment transaction. The benchmark result does not reflect our actual corporate borrowing spread or deposit rate, so the amount is a reference rather than a guaranteed offer.

The euro put provides a minimum net amount of $1,835,320 and allows the company to participate in euro appreciation. The $32,980 upfront premium is the cost of retaining this flexibility. If the euro appreciates by 5%, net proceeds increase to $1,928,735. While the option offers meaningful downside protection, it provides a lower floor than the benchmark money-market hedge and requires cash today. The option premium is also an assigned scenario value rather than a refreshed executable quote.

Remaining unhedged avoids explicit hedging costs but exposes the entire receivable to exchange-rate movements. A 5% decline in the euro reduces proceeds to $1,774,885, while a 5% increase raises proceeds to $1,961,715. The $186,830 difference between these outcomes is significant for budgeting. The hypothetical euro call is excluded from the recommendation because it protects a payable, not our receivable; its modeled maximum payable cost is $1,918,620 including the premium.

## C. Sensitivity interpretation

| Terminal EUR/USD | EUR −5% | Unchanged | EUR +5% |
|---|---:|---:|---:|
| Rate | 1.04405 | 1.09900 | 1.15395 |
| Forward | $1,989,850 | $1,989,850 | $1,989,850 |
| Money market | $1,878,869 | $1,878,869 | $1,878,869 |
| Put, net | $1,835,320 | $1,835,320 | $1,928,735 |
| Unhedged | $1,774,885 | $1,868,300 | $1,961,715 |

The forward and money-market hedge remove exchange-rate variability, whereas the put reduces downside exposure while retaining upside. In the depreciation scenario, the put improves proceeds by $60,435 relative to remaining unhedged. At unchanged spot or above the strike, the put costs $32,980 relative to unhedged proceeds under the model convention. It therefore represents insurance rather than a way to maximize proceeds in every scenario.

At the assigned forward rate, unhedged proceeds exceed forward proceeds only above 1.1705, and put proceeds exceed them only above 1.1899. Both thresholds lie outside the tested ±5% range. This does not establish that appreciation beyond the range is impossible. If a fresh forward instead equals the CIP benchmark of 1.1052168112, the put would outperform it above approximately 1.1246168112, within the tested range. The actual quote is consequently material to the opportunity cost of certainty.

## D. Recommendation

I recommend pursuing a 182-day forward sale of the full EUR 1.7 million receivable, subject to confirming executable pricing and settlement terms. The forward is consistent with the company's primary objective of cash-flow stability, and it avoids the stated upfront option premium and the need to arrange a separate euro loan. I would not authorize execution based solely on the original scenario quote.

The November 20 covered interest parity calculation implies a forward rate of 1.1052168112, compared with the assigned bank rate of 1.1705. The difference is 0.0652831888 USD/EUR, or approximately 652.83 pips and $110,981.42 on our receivable. The assigned quote would exceed the money-market benchmark by more than the $50,000 initially hypothesized, but that hypothesis remains unconfirmed on an executable basis. The most plausible explanation is the comparison of an undated scenario quote with later reference data; benchmark funding differences, maturity mismatch and bid-ask spreads also limit comparability. The available evidence does not establish how much each factor contributes.

The gap changes the expected dollar proceeds and confidence in the quote, but not the initial preference for a forward as the simplest way to secure our budget. Treasury should request a firm 182-day EUR-selling forward bid, comparable borrowing and investment rates, and a current put quote. If the net forward proceeds meet the CFO's budget requirement and compare favorably with executable money-market proceeds, execute the forward. If not, return to the CFO with the revised comparison before committing. No minimum budget threshold has been supplied, so this memo does not invent one.

## E. Executive justification

A forward provides a known settlement amount without requiring the company to pay an option premium upfront. This allows management to plan payroll, software development and other dollar expenditures with greater confidence. A money-market hedge may achieve comparable certainty but could consume credit capacity and create additional operational and balance-sheet requirements. A put is preferable only if management places sufficient value on upside participation to justify its premium and lower guaranteed proceeds. No documented board view on euro appreciation has been provided, so the recommendation prioritizes the stated cash-flow protection objective rather than an unsupported currency forecast.

Treasury should confirm the customer's payment date, counterparty limits, collateral or margin requirements, settlement instructions and any fees. If payment is delayed or reduced, a full forward could leave the company with an obligation to deliver euros it has not received. The hedge should therefore be matched to the confirmed invoice and monitored until settlement. Accounting treatment should be reviewed separately if hedge accounting is desired.

**Decision requested:** authorize Treasury to obtain executable quotes and prepare a full-notional forward for approval, not to transact at the unverified assigned rate. Final execution remains subject to the completed validation and quote comparison.

**Supporting records:** Stage 4 market-data memo (2026-11-20), Stage 4 workbook and Stage 5 validation analysis (2026-11-28). Market inputs are dated reference proxies; the fresh-session response matches all twelve stored receivable scenario results and three independently calculated call costs. Personal calculator sign-off, call worksheet scenario verification and executable quotes remain outstanding.
