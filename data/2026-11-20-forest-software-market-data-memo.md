# Forest Software — Stage 4 Market-Data and Validation Memo

**Market observation date:** Friday, 2026-11-20. **Retrieved:** 2026-11-21 (HST; exact retrieval clock time not retained). **Currency convention:** USD per EUR. **Scenario:** Assigned Scenario 21, EUR 1,700,000 receivable in 182 calendar days. **Status:** Provisional; executable bank quote and external lab cross-check outstanding.

## Market input register

| Named range | Value | Observation date / source | Selection and limitations |
|---|---:|---|---|
| `FC_AMT` | 1,700,000 EUR | Assigned Forest Software Scenario 21 | Contractual hypothetical receivable; not market data |
| `S0_in` | 1.0990 USD/EUR | ECB, *Euro foreign exchange reference rates*, 2026-11-20; https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html | ECB reference fixing around 14:10 CET, generally published 16:00 CET. **Not** an end-of-New-York-day closing quote or executable spot quote. Used as a reproducible same-day reference proxy. |
| `F0_in` | 1.1705 USD/EUR | Assigned Scenario 21 indicative bank forward; date of original quote not provided | Kept unchanged; **not** a live November 20 bank quote. Bank requote required. |
| `R_USD` | 0.0451 (4.51%) | U.S. Treasury 1-year constant-maturity par yield, 2026-11-20, as reported from Treasury data by https://lzzo.com/bonds/united-states/1-year | Government-rate proxy, not executable USD deposit/lending rate; verify original Treasury series if required. |
| `R_FC` | 0.03372 (3.372%) | Bank of Finland, *Euribor interest rates*, 12-month fixing, 2026-11-20; https://www.suomenpankki.fi/en/statistics/interest-rates-and-exchange-rates/euribor-rates/ | Unsecured interbank benchmark, not Forest Software's EUR borrowing rate. Maturity mismatch: 12 months versus 182-day hedge. |
| `K_PUT` | 1.0990 USD/EUR | Computed equal to `S0_in`, 2026-11-20 | At-the-money strike assumption; not an executable option listing. |
| `K_CALL` | 1.0990 USD/EUR | Computed equal to `S0_in`, 2026-11-20 | At-the-money strike assumption for illustrative EUR payable, not the actual receivable hedge. |
| `PREM_PUT` | 0.0194 USD/EUR | Assigned Scenario 21 | Scenario premium retained; **not** a current option quote. Total premium USD 32,980. |
| `PREM_CALL` | 0.0296 USD/EUR | Assigned Scenario 21 | Scenario premium retained; **not** a current option quote. Total premium USD 50,320. |
| `T_DAYS` | 182 days | Assigned Scenario 21 | ACT/360 simple interest; T = 182/360 years. |

**Timestamp limitation:** The source observation dates are established, but the precise retrieval time was not recorded. The ECB fixing time is an observation convention, not the retrieval time. This register therefore does not claim a minute-accurate retrieval audit trail.

## Covered interest parity and material discrepancy

Using the assignment's formula:

`F_CIP = S0_in × (1 + R_USD × T_DAYS / 360) / (1 + R_FC × T_DAYS / 360)`

`= 1.0990 × (1 + 0.0451 × 182 / 360) / (1 + 0.03372 × 182 / 360)`

**CIP-implied forward: 1.1052168112 USD/EUR.** Assigned bank forward: **1.1705000000**. Bank minus CIP: **+0.0652831888 USD/EUR** (approximately **652.83 pips**), or **+$110,981.42** for EUR 1,700,000. CIP-implied proceeds: **$1,878,868.58**. Scenario forward proceeds: **$1,989,850.00**. This gap is not proof of executable arbitrage: the scenario quote is undated, spot is an ECB reference fixing, and benchmark rates do not represent matched borrowing and lending rates. Obtain a same-time 182-day EUR/USD bank forward and corresponding executable funding rates before concluding the quote is wrong.

## Model population and structural checks

Updated only the five market-sensitive input cells `Inputs!B7`, `B9`, `B10`, `B11`, `B12`, preserving `F0_in`, both scenario premiums, receivable, and tenor. Added a `Live_CIP_Audit` tab with formula-linked CIP calculation, USD difference, and an explicit REVIEW status. Updated provenance annotations on `Inputs`. Original named-range contract, hedge formulas, sensitivity worksheet and chart were retained in the exported workbook.

**Outstanding checks:** The Stage 3 workbook's fixed placeholder check figures were calibrated to its old inputs. They are not universal identities and must not be made to PASS by changing market data. Their expected REVIEW status after live-data substitution is not itself a model failure. The sensitivity chart should be opened in desktop Excel, calculation enabled, and visually checked for 11 scenarios centered on 1.0990. A manual Excel recalc and the external FX Hedging Lab cross-check were **not completed**, so this memo does **not** certify that all formulas and outputs agree with the lab.

## Independent mathematical checks

- Forward: EUR 1,700,000 × 1.1705 = **USD 1,989,850.00**.
- Money market (using benchmark proxies): `EUR 1,700,000/(1+0.03372×182/360) × 1.0990 × (1+0.0451×182/360)` = **USD 1,878,868.58**, equal to CIP-implied forward proceeds by construction.
- Put minimum net proceeds: EUR 1,700,000 × (1.0990 − 0.0194) = **USD 1,835,320.00**.
- Hypothetical call payable maximum: EUR 1,700,000 × (1.0990 + 0.0296) = **USD 1,918,620.00**. The call is not a receivable hedge.

**Cross-check required before submission:** Visit https://adamwstauffer.github.io/ai-lms/fxlab.html and enter the inputs in the register. Record the lab's forward, money-market and put results and compare against the independently calculated values above; investigate any discrepancies. No lab comparison is claimed here.

## Audit conclusion

The sourced reference inputs reveal a **material inconsistency** between the original scenario bank forward and the CIP benchmark. The workbook has been populated without manipulating that quote. **Provisional / not fully validated** pending a current bank requote, desktop Excel recalculation and chart inspection, and the external lab comparison. Do not characterize the model as fully verified until those steps are documented.
