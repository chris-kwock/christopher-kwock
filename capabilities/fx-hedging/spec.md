---
type: spec
title: "FX Hedging Model Specification — Forest Software"
scenario: "forest-software"
date: 2026-11-07
version: "1.0"
status: "Draft for Treasury Review"
llm_used: "OpenAI GPT-6"
---

# FX Hedging Model Specification — Forest Software

**Created by:** Christopher Kwock  
**Updated by:** Christopher Kwock  
**Date Created:** 2026-11-07  
**Date Updated:** 2026-11-07  
**Version:** 1.0  
**LLM Used:** OpenAI GPT-6  

---

## 1. Problem Statement

Forest Software is a U.S.-based software company that expects to receive EUR 1,700,000 from a Finnish customer in 182 days. Because the company reports its financial results in U.S. dollars, the value of this receivable will depend on the EUR/USD exchange rate at settlement. If the euro depreciates against the U.S. dollar, the company will receive fewer dollars when converting the payment, potentially reducing operating cash flow and profitability.

The purpose of this model is to evaluate different foreign exchange hedging strategies to reduce this uncertainty. The model will compare an unhedged position, a forward contract, a money-market hedge, and a currency put option. A currency call option will also be included as a separate comparison for a foreign-currency payable.

The model will calculate the USD proceeds under each strategy, evaluate their performance under different exchange-rate scenarios, and identify the tradeoffs between guaranteed proceeds, hedging costs, and potential upside. The results will provide Treasury with a consistent framework for selecting a strategy based on the company's risk tolerance and cash-flow requirements.

The initial model will use indicative market assumptions, which will be replaced with verified market data during Stage 4.

## 2. Inputs: Named-Range Contract

The workbook will use the following eleven required named ranges. These names must be used exactly throughout the model to maintain consistency between the specification, Excel formulas, and automated validation checks.

| Named Range | Placeholder Value | Unit | Stage 4 Data Source |
|---|---:|---|---|
| `FC_AMT` | 1700000 | EUR | Assigned scenario and company receivable records |
| `S0_in` | 1.1700 | USD/EUR | Current EUR/USD spot quotation from a bank or market-data provider |
| `F0_in` | 1.1705 | USD/EUR | Executable 182-day EUR/USD forward quotation from a bank |
| `R_USD` | 4.00% | Annual rate | Federal Reserve H.15 or comparable USD money-market benchmark |
| `R_FC` | 3.914% | Annual rate | ECB or comparable EUR money-market benchmark |
| `K_PUT` | 1.1700 | USD/EUR | Bank quotation for a EUR put option |
| `K_CALL` | 1.1700 | USD/EUR | Bank quotation for a EUR call option |
| `PREM_PUT` | 0.0194 | USD per EUR | Bank quotation for a EUR put premium |
| `PREM_CALL` | 0.0296 | USD per EUR | Bank quotation for a EUR call premium |
| `T_DAYS` | 182 | Calendar days | Assigned settlement schedule |

**Placeholder Disclosure:** All exchange rates, interest rates, strikes, and premiums are indicative and will be replaced with live market data at Stage 4. The receivable amount and settlement horizon are assigned scenario parameters. The initial spot rate and interest rates are illustrative assumptions selected for model development and testing.

All named ranges must refer to a single input cell on the Inputs worksheet. Interest rates must be entered as decimals, meaning 4.00% is stored as 0.04. Exchange rates must be expressed in USD per EUR.

Input cells will be highlighted yellow, while calculated outputs will be highlighted gray. Currency amounts will be displayed to two decimal places, exchange rates to four decimal places, and interest rates as percentages. Calculations must retain full precision regardless of the displayed format.

## 3. Tab Architecture

The workbook will contain nine worksheets organized to separate inputs, calculations, validation, and presentation.

| Worksheet | Purpose |
|---|---|
| `Cover` | Executive summary of the exposure, hedge results, and comparison |
| `Legend_Key` | Explanation of color coding, named ranges, units, and formatting |
| `Inputs` | Central location for all eleven required named inputs |
| `Forward_Hedge` | Forward hedge calculations and locked USD proceeds |
| `Money_Market_Hedge` | Three-step money-market hedge calculations |
| `Option_Hedge` | Put and call option calculations, premiums, and net proceeds |
| `Parity_Check` | Covered interest rate parity calculations and validation |
| `Sensitivity` | Exchange-rate scenarios, proceeds comparison, and chart |
| `Notes_Assumptions` | Assumptions, limitations, sources, and methodology |

### Cover

The Cover worksheet will summarize Forest Software's EUR 1,700,000 receivable, settlement horizon, and available hedging alternatives. It will display the forward proceeds, money-market proceeds, put hedge floor, option premium, and parity validation status.

The summary will explain the primary tradeoffs between exchange-rate certainty, protection against depreciation, and participation in favorable exchange-rate movements.

### Legend and Inputs

The Legend_Key worksheet will explain the workbook's formatting conventions. Yellow cells will represent editable assumptions, gray cells will represent calculated outputs, and validation cells will display PASS or REVIEW.

The Inputs worksheet will contain all required named ranges. Other worksheets must reference these named inputs rather than duplicate assumptions or use hard-coded values.

### Calculation Worksheets

Each hedging strategy will have a separate calculation area. Intermediate calculations must be visible so an auditor can trace how each result was obtained.

The money-market hedge must show borrowing, currency conversion, and USD investment as three separate steps.

### Sensitivity and Documentation

The Sensitivity worksheet will contain eleven exchange-rate scenarios and one line chart comparing the four receivable strategies.

The Notes_Assumptions worksheet will document the calculation conventions, simplifying assumptions, market-data sources, and limitations.

## 4. Assumptions and Constraints

### Interest-Rate Convention

All interest calculations will use simple interest with an ACT/360 day-count convention.

The year fraction will be calculated as:

`Year_Fraction = T_DAYS / 360`

For the assigned scenario, the settlement period is 182 calendar days.

No continuous compounding or alternative day-count convention will be used in the initial model.

### Borrowing and Lending Rates

The model assumes that the stated annual USD and EUR rates can be used for the relevant borrowing and investment transactions.

The initial model uses the same rate for borrowing and lending within each currency. This is a simplifying assumption because actual borrowing and deposit rates may differ.

Stage 4 will identify the market instruments underlying each rate and document differences between benchmark rates and executable financing terms.

### Forward Contract

The forward contract will cover the entire EUR 1,700,000 receivable and settle on the expected payment date.

The forward rate will remain fixed after inception. No separate upfront premium will be assumed.

Transaction costs, credit exposure, collateral requirements, and bid-ask spreads will be excluded from the initial calculation.

### Money-Market Hedge

The company is assumed to be able to borrow euros today, convert the borrowed euros to USD at the initial spot rate, and invest the USD until settlement.

The EUR borrowing amount will be sized so that the receivable exactly repays the EUR loan, including interest, at settlement.

### Covered Interest Rate Parity

The model will use covered interest rate parity as a theoretical benchmark.

Under consistent rates, maturities, and market conventions, the forward rate should approximately equal the rate implied by the money-market hedge.

Differences must be calculated and displayed rather than eliminated through rounding or manual adjustments.

### Currency Options

The EUR put and call options are assumed to be European-style options expiring on the receivable settlement date.

The initial strikes will be set equal to the illustrative spot rate of 1.1700 USD/EUR.

The put option will protect the EUR receivable against depreciation while allowing the company to benefit from appreciation.

The call option will be included only as a comparison for a EUR payable because it does not provide the appropriate downside protection for Forest Software's receivable.

### Premium Treatment

Option premiums are paid at inception. However, the model will deduct the total premium directly from settlement proceeds for the simplified comparison required by the assignment.

The initial model will not calculate the financing cost or future value of the upfront premium.

This simplification must be disclosed because it does not represent the exact economic settlement-date cost of the option.

### Other Constraints

The model assumes the customer pays the full receivable on the scheduled settlement date.

Transaction fees, taxes, counterparty default risk, collateral costs, and hedge-accounting effects are excluded.

The model compares nominal USD proceeds rather than risk-adjusted present values.

## 5. Calculation Flow

All calculations must reference named ranges rather than cell addresses. Intermediate results must be calculated separately where specified.

### 5.1 Unhedged Position

Define `S_T` as the EUR/USD spot exchange rate at settlement.

The unhedged proceeds are calculated as:

`Unhedged_Proceeds = FC_AMT * S_T`

The company receives the full EUR receivable and converts it at the prevailing settlement spot rate.

A stronger euro increases USD proceeds, while a weaker euro reduces proceeds.

### 5.2 Forward Hedge

The forward hedge locks in the USD value of the receivable at inception.

Formula:

`Forward_Proceeds = FC_AMT * F0_in`

Using the illustrative inputs:

`Forward_Proceeds = 1700000 * 1.1705`

**Expected Result: $1,989,850.00**

The proceeds must remain constant regardless of changes in the settlement exchange rate.

The forward hedge provides certainty but eliminates the opportunity to benefit from euro appreciation.

### 5.3 Money-Market Hedge

The money-market hedge will be calculated using three separate steps.

**Step 1: Borrow EUR Today**

Borrow the present value of the future EUR receivable.

`FC_Borrow = FC_AMT / (1 + R_FC * T_DAYS / 360)`

Using the illustrative assumptions:

`FC_Borrow = 1700000 / (1 + 0.03914 * 182 / 360)`

Expected result:

`FC_Borrow = €1,667,014.05`

The loan must grow to EUR 1,700,000 at settlement so the receivable can repay the entire borrowing.

**Step 2: Convert EUR to USD**

Convert the borrowed EUR into USD at the initial spot rate.

`USD_Now = FC_Borrow * S0_in`

Expected result:

`USD_Now = $1,950,406.44`

**Step 3: Invest USD Until Settlement**

Invest the converted USD amount at the annual USD interest rate.

`MM_Proceeds = USD_Now * (1 + R_USD * T_DAYS / 360)`

Expected result:

`MM_Proceeds = $1,989,847.99`

Each step must appear in a separate calculated output cell.

The money-market hedge provides a predetermined USD amount under the model assumptions.

### 5.4 Covered Interest Rate Parity

The implied forward rate will be calculated as:

`F_implied = S0_in * (1 + R_USD * T_DAYS / 360) / (1 + R_FC * T_DAYS / 360)`

Expected result:

`F_implied = 1.17049882`

The difference between the implied and quoted forward rates will be calculated as:

`Parity_Difference = F_implied - F0_in`

Expected result:

`Parity_Difference = -0.00000118`

The difference in hedge proceeds will be calculated as:

`Proceeds_Difference = MM_Proceeds - Forward_Proceeds`

Expected result:

`Proceeds_Difference = -$2.01`

The model must display these differences and evaluate them using the validation rules in Section 7.

### 5.5 EUR Put Option Hedge

The company purchases a EUR put option to establish a minimum exchange rate while retaining the ability to benefit from euro appreciation.

First calculate the total option premium:

`Put_Premium_Total = FC_AMT * PREM_PUT`

Expected result:

`Put_Premium_Total = $32,980.00`

Calculate gross USD proceeds:

`Put_Gross_Proceeds = FC_AMT * MAX(S_T, K_PUT)`

Calculate net USD proceeds:

`Put_Net_Proceeds = Put_Gross_Proceeds - Put_Premium_Total`

Equivalent formula:

`Put_Net_Proceeds = FC_AMT * MAX(S_T, K_PUT) - FC_AMT * PREM_PUT`

If the settlement exchange rate is below the strike, the company exercises the put and receives the strike-based proceeds.

If the settlement rate is above the strike, the company allows the put to expire and converts the EUR receivable at the more favorable market rate.

The premium is deducted in both cases.

The minimum net proceeds are:

`Put_Floor = FC_AMT * (K_PUT - PREM_PUT)`

Expected result:

`Put_Floor = $1,956,020.00`

### 5.6 EUR Call Option Comparison

The EUR call option will be modeled separately as protection for a EUR payable.

Calculate the total call premium:

`Call_Premium_Total = FC_AMT * PREM_CALL`

Expected result:

`Call_Premium_Total = $50,320.00`

Calculate the USD cost of purchasing EUR under the call strategy:

`Call_Net_Cost = FC_AMT * MIN(S_T, K_CALL) + Call_Premium_Total`

Calculate the maximum USD cost:

`Call_Max_Cost = FC_AMT * (K_CALL + PREM_CALL)`

Expected result:

`Call_Max_Cost = $2,039,320.00`

The call comparison must be labeled as a payable cost and excluded from the ranking of Forest Software's receivable hedges.

## 6. Sensitivity Analysis Plan

The Sensitivity worksheet will evaluate the effect of different settlement exchange rates on each receivable strategy.

### Scenario Range

The analysis will begin at 95% of the initial spot rate and end at 105% of the initial spot rate.

The model will use 1% increments, producing exactly eleven scenarios.

For each integer `i` from -5 to +5:

`S_T(i) = S0_in * (1 + i / 100)`

Using the illustrative spot rate of 1.1700, the scenario range is 1.1115 to 1.2285 USD/EUR.

The scenario values must update automatically if `S0_in` changes.

### Sensitivity Table

The table will include the following columns:

| Column | Calculation |
|---|---|
| Spot Change (%) | -5% through +5% |
| Settlement Spot Rate | `S_T` |
| Unhedged Proceeds | `FC_AMT * S_T` |
| Forward Proceeds | `FC_AMT * F0_in` |
| Money-Market Proceeds | `MM_Proceeds` |
| Put Net Proceeds | `FC_AMT * MAX(S_T, K_PUT) - FC_AMT * PREM_PUT` |

The forward and money-market proceeds must remain constant across all scenarios.

The unhedged proceeds must increase linearly as the euro appreciates.

The put hedge must establish a minimum net proceeds floor while allowing upside participation above the strike.

### Comparison Chart

The workbook will include one line chart titled:

**USD Proceeds by EUR/USD Settlement Rate**

The horizontal axis will represent the settlement spot exchange rate in USD/EUR.

The vertical axis will represent USD proceeds.

The chart will include four series:

- Unhedged
- Forward
- Money-Market
- Put Hedge

The forward and money-market lines should be approximately horizontal and nearly overlap.

The unhedged line should slope upward as the euro appreciates.

The put hedge should display a flat floor below the strike and increase above the strike.

### CFO Interpretation

The sensitivity analysis should allow the CFO to evaluate the tradeoff between downside protection and potential upside.

The forward and money-market hedges provide cash-flow certainty, while the put hedge protects against depreciation and preserves the potential benefit of appreciation.

The unhedged position may produce the highest proceeds if the euro strengthens but creates the greatest exposure to depreciation.

The chart should help Treasury evaluate which strategy best matches the company's risk tolerance and cash-flow needs rather than automatically selecting the highest outcome in a single scenario.

## 7. Validation Rules and Check Figures

The completed workbook must pass the following validation tests before it is accepted for Stage 3.

### 7.1 Input Validation

All eleven required named ranges must exist and reference the correct input cells.

`FC_AMT` must be greater than zero.

`S0_in`, `F0_in`, `K_PUT`, and `K_CALL` must be positive.

`PREM_PUT` and `PREM_CALL` must be nonnegative.

`T_DAYS` must be a positive whole number.

Interest rates must be stored as decimal values and must produce positive accumulation factors.

No calculation may rely on hard-coded market assumptions.

### 7.2 Forward Hedge Validation

The forward hedge must produce:

`Forward_Proceeds = $1,989,850.00`

This result must remain constant across all settlement spot scenarios.

### 7.3 Money-Market Hedge Validation

The model must produce the following check figures using the illustrative inputs:

| Calculation | Expected Result |
|---|---:|
| EUR Borrowed | €1,667,014.05 |
| USD Converted Today | $1,950,406.44 |
| USD at Settlement | $1,989,847.99 |

The EUR loan balance at settlement must equal EUR 1,700,000, subject only to display rounding.

All three money-market steps must be visible as separate calculations.

### 7.4 Covered Interest Rate Parity Validation

The implied forward rate should be approximately:

`F_implied = 1.17049882`

The quoted forward rate is:

`F0_in = 1.1705`

The model must calculate:

`Parity_Difference = F_implied - F0_in`

For the initial placeholder scenario, the parity-rate test passes if:

`ABS(Parity_Difference) <= 0.00001`

The proceeds-based test passes if:

`ABS(MM_Proceeds - Forward_Proceeds) <= 20`

The workbook must display `PASS` only when both tests pass.

Otherwise, the workbook must display `REVIEW`.

These tolerances apply to the initial illustrative assumptions. Actual market-data differences may reflect funding spreads, bid-ask spreads, or other market frictions and must be investigated separately.

### 7.5 Put Option Validation

The total put premium must equal:

`Put_Premium_Total = $32,980.00`

The minimum net proceeds must equal:

`Put_Floor = $1,956,020.00`

When `S_T < K_PUT`, put proceeds must remain at the floor.

When `S_T > K_PUT`, put proceeds must increase as the settlement exchange rate increases.

At `S_T = K_PUT`, both payoff branches must produce the same result.

### 7.6 Call Option Validation

The total call premium must equal:

`Call_Premium_Total = $50,320.00`

The maximum USD cost for the illustrative payable must equal:

`Call_Max_Cost = $2,039,320.00`

When `S_T > K_CALL`, the call must cap the USD payable cost.

When `S_T < K_CALL`, the payable cost must reflect the lower market exchange rate plus the premium.

### 7.7 Sensitivity Validation

The sensitivity table must contain exactly eleven scenarios.

The first settlement spot rate must equal:

`0.95 * S0_in`

The final settlement spot rate must equal:

`1.05 * S0_in`

The middle scenario must equal:

`S0_in`

The change between consecutive scenarios must equal one percentage point.

Forward and money-market proceeds must remain constant across all scenarios.

Unhedged proceeds must increase as `S_T` increases.

Put proceeds must never fall below the calculated put floor.

### 7.8 Sensitivity Check Figures

Using the illustrative assumptions, the workbook should produce the following results:

| Spot Change | Settlement Spot | Unhedged | Forward | Money-Market | Put Net |
|---|---:|---:|---:|---:|---:|
| -5% | 1.1115 | $1,889,550 | $1,989,850 | $1,989,848 | $1,956,020 |
| 0% | 1.1700 | $1,989,000 | $1,989,850 | $1,989,848 | $1,956,020 |
| +5% | 1.2285 | $2,088,450 | $1,989,850 | $1,989,848 | $2,055,470 |

Money-market values are rounded to the nearest dollar in this table. The workbook must retain full calculation precision.

### 7.9 Audit Completion Criteria

The workbook will be ready for Treasury review when all required named ranges exist, formulas produce the expected check figures, the sensitivity table updates dynamically, and the chart accurately represents the calculated proceeds.

Any validation failures must be investigated and documented before the model is accepted.

## 8. Required Outputs

All calculated results must be displayed in gray output cells. The output labels below must be used consistently throughout the workbook.

### Cover Summary Outputs

| Output Name | Description |
|---|---|
| `Initial_USD_Value` | EUR receivable valued at initial spot |
| `Forward_Proceeds` | Locked USD proceeds from forward hedge |
| `MM_Proceeds` | USD proceeds from money-market hedge |
| `Put_Floor` | Minimum net USD proceeds from put hedge |
| `Put_Premium_Total` | Total initial put premium |
| `Parity_Status` | PASS or REVIEW parity validation |

### Forward Hedge Outputs

| Output Name | Description |
|---|---|
| `Forward_Proceeds` | Fixed USD proceeds at settlement |
| `Forward_Locked_Rate` | Contractual forward exchange rate |

### Money-Market Hedge Outputs

| Output Name | Description |
|---|---|
| `FC_Borrow` | EUR borrowed at inception |
| `USD_Now` | USD obtained from spot conversion |
| `MM_Proceeds` | USD investment value at settlement |

### Option Hedge Outputs

| Output Name | Description |
|---|---|
| `Put_Premium_Total` | Total put premium |
| `Put_Gross_Proceeds` | Gross proceeds under put strategy |
| `Put_Net_Proceeds` | Net proceeds after put premium |
| `Put_Floor` | Minimum net put proceeds |
| `Call_Premium_Total` | Total call premium |
| `Call_Net_Cost` | USD cost of hedged EUR payable |
| `Call_Max_Cost` | Maximum USD cost under call hedge |

### Parity Check Outputs

| Output Name | Description |
|---|---|
| `F_implied` | Forward rate implied by interest rate parity |
| `Parity_Difference` | Implied forward less quoted forward |
| `Proceeds_Difference` | Money-market less forward proceeds |
| `Parity_Status` | PASS or REVIEW result |

### Sensitivity Outputs

The Sensitivity worksheet must contain an eleven-row table showing the settlement exchange rate and USD proceeds for the unhedged, forward, money-market, and put strategies.

The worksheet must also include one line chart comparing the four strategies.

All outputs must recalculate automatically when the named inputs change.

### Model Completion Requirements

The finished workbook must contain all nine specified worksheets, use the eleven required named ranges, separate inputs from calculations, and preserve full precision.

The workbook must also include the required validation checks, sensitivity analysis, comparison chart, and documentation of assumptions.

The final workbook must be saved as:

`capabilities/fx-hedging/model.xlsx`

The specification must be saved as:

`capabilities/fx-hedging/spec.md`

The folder README must explain the purpose of both files and provide instructions for reviewing the model.

---

## AI Review and Revision Record

**Review Date:** 2026-11-07  
**AI Tool:** OpenAI GPT-6  
**Purpose:** Identify missing requirements, ambiguous calculations, and potential errors before building the Excel workbook.

### Initial Review Request

Review the FX hedging model specification for Forest Software. Identify missing assumptions, unclear calculation instructions, inconsistent formulas, incomplete validation rules, and other weaknesses that could cause an AI to construct the workbook incorrectly.

### Finding 1: Interest-Rate Convention

**Before:** Calculate interest earned on the USD investment until settlement.

**Issue:** The instruction did not specify the day-count convention or compounding method.

**After:** Calculate interest using simple interest and ACT/360:

`USD_Now * (1 + R_USD * T_DAYS / 360)`

**Decision:** Accepted. The revision makes the interest calculation consistent and removes ambiguity.

### Finding 2: Option Premium Timing

**Before:** Subtract the option premium from settlement proceeds.

**Issue:** The instruction did not distinguish between the upfront premium payment and its treatment in the model.

**After:** The premium is paid at inception but deducted directly from settlement proceeds under the simplified course convention. Premium financing costs are excluded and disclosed.

**Decision:** Accepted. The revision clarifies the model's assumptions without changing the required formula.

### Finding 3: Call Option Treatment

**Before:** Compare forward, money-market, put, and call hedges.

**Issue:** A EUR call is appropriate for protecting a EUR payable rather than the company's EUR receivable.

**After:** Compare the unhedged, forward, money-market, and put strategies for the receivable. Include the call separately as a payable hedge comparison.

**Decision:** Accepted. This prevents the workbook from comparing strategies designed for different currency exposures.

### Finding 4: Parity Validation

**Before:** Verify that forward and money-market proceeds are approximately equal.

**Issue:** The instruction did not define what constitutes an acceptable difference.

**After:** Calculate the implied forward-rate difference and proceeds difference separately. Apply illustrative tolerances of 0.00001 USD/EUR and $20, respectively, and display PASS or REVIEW.

**Decision:** Accepted with qualification. These tolerances are appropriate for the initial placeholder scenario but must be reviewed when live market data are introduced.

### Review Summary

The review identified areas where the initial specification could have resulted in inconsistent formulas or incorrect comparisons.

The revisions provide clearer interest-rate conventions, more accurate treatment of option premiums, appropriate separation of receivable and payable hedges, and measurable validation criteria.

These changes should make the Stage 3 workbook easier to construct and audit.

---

## Final Design Summary

This specification establishes the requirements for Forest Software's foreign exchange hedging model. The model will compare the financial outcomes of an unhedged position, a forward contract, a money-market hedge, and a EUR put option.

Under the illustrative assumptions, the forward hedge provides approximately $1.99 million in locked USD proceeds, while the money-market hedge produces a nearly identical amount. The put hedge provides a lower minimum amount but allows the company to benefit from favorable exchange-rate movements.

The sensitivity analysis will help Treasury evaluate the tradeoffs between cash-flow certainty, hedging costs, and upside participation.

The final strategy will depend on Forest Software's risk tolerance, liquidity requirements, and market conditions. The model will provide a consistent and auditable framework for making that decision.

**Next Stage:** Build `model.xlsx` according to this specification, validate the results against the check figures, and replace the indicative assumptions with verified market data during Stage 4.
