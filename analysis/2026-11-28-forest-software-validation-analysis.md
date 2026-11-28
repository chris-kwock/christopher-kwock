# Stage 5 — Forest Software Validation Analysis

Date: 2026-11-28 | Scenario 21 | Market observation: 2026-11-20

**Status: numerical validation complete; execution and manual sign-off outstanding.** The original Stage 2 specification and user-supplied fresh-chat response are now available. Twelve stored workbook scenario outputs agree with the fresh LLM to the cent; three call payable outcomes agree with independent arithmetic but are not directly verified against workbook scenario cells.

## 1. Independent production test

The user supplied the fresh-chat response, preserved verbatim in `evidence/stage5-fresh-llm-response.txt`. It reports using only the Stage 2 specification and Stage 4 memo. The requested prompt was: “Compute all hedge outcomes and recommend a strategy using the two attached documents.” Exact model, run timestamp and session settings were not independently verified. The Stage 4 memo contains check figures, so agreement alone does not establish independent derivation.

## 2. Comparison and reconciliation

USD amounts rounded to cents. Delta is LLM minus stored workbook; tolerance $0.01. Call amounts are hypothetical payable costs, not receivable proceeds.

| S_T | Strategy | Workbook | Fresh LLM | Independent arithmetic | Delta | Diagnosis |
|---:|---|---:|---:|---:|---:|---|
| 1.04405 | Forward | 1,989,850.00 | 1,989,850.00 | 1,989,850.00 | 0.00 | Workbook match |
| 1.04405 | Money market | 1,878,868.58 | 1,878,868.58 | 1,878,868.58 | 0.00 | Workbook match |
| 1.04405 | Put | 1,835,320.00 | 1,835,320.00 | 1,835,320.00 | 0.00 | Workbook match |
| 1.04405 | Call payable | Not in sensitivity table | 1,825,205.00 | 1,825,205.00 | N/A | Formula match |
| 1.04405 | Unhedged | 1,774,885.00 | 1,774,885.00 | 1,774,885.00 | 0.00 | Workbook match |
| 1.09900 | Forward | 1,989,850.00 | 1,989,850.00 | 1,989,850.00 | 0.00 | Workbook match |
| 1.09900 | Money market | 1,878,868.58 | 1,878,868.58 | 1,878,868.58 | 0.00 | Workbook match |
| 1.09900 | Put | 1,835,320.00 | 1,835,320.00 | 1,835,320.00 | 0.00 | Workbook match |
| 1.09900 | Call payable | Not in sensitivity table | 1,918,620.00 | 1,918,620.00 | N/A | Formula match |
| 1.09900 | Unhedged | 1,868,300.00 | 1,868,300.00 | 1,868,300.00 | 0.00 | Workbook match |
| 1.15395 | Forward | 1,989,850.00 | 1,989,850.00 | 1,989,850.00 | 0.00 | Workbook match |
| 1.15395 | Money market | 1,878,868.58 | 1,878,868.58 | 1,878,868.58 | 0.00 | Workbook match |
| 1.15395 | Put | 1,928,735.00 | 1,928,735.00 | 1,928,735.00 | 0.00 | Workbook match |
| 1.15395 | Call payable | Not in sensitivity table | 1,918,620.00 | 1,918,620.00 | N/A | Formula match |
| 1.15395 | Unhedged | 1,961,715.00 | 1,961,715.00 | 1,961,715.00 | 0.00 | Workbook match |

No numerical discrepancies were observed in the tested outcomes. The fresh response correctly prioritized Stage 4 inputs, retained ACT/360 and face-value premiums, and excluded the call from receivable ranking. The stored parity check reports REVIEW, as do fixed placeholder money-market, put and call checks after inputs changed. These are market-input and benchmark-design issues, not demonstrated formula errors. The call scenario comparison remains incomplete at workbook-cell level.

## 3. Calculator verification (no Excel)

The following arithmetic was independently recomputed outside Excel; reproduce it on a calculator before certifying personal verification. Keep full precision until the final amount.

| Outcome / step | Named-range expression and substitution | Result |
|---|---|---:|
| Tenor | T_DAYS / 360 = 182 / 360 | 0.5055555556 |
| Forward | FC_AMT × F0_in = 1,700,000 × 1.1705 | $1,989,850.00 |
| MM 1: borrow EUR | FC_AMT / (1 + R_FC × T_DAYS / 360) = 1,700,000 / (1 + 0.03372 × 182 / 360) | €1,671,505.292117 |
| MM 2: convert | EUR loan × S0_in = 1,671,505.292117 × 1.0990 | $1,836,984.316036 |
| MM 3: invest USD | USD proceeds × (1 + R_USD × T_DAYS / 360) = 1,836,984.316036 × (1 + 0.0451 × 182 / 360) | $1,878,868.58 |
| MM repayment | EUR loan × (1 + 0.03372 × 182 / 360) | €1,700,000.00 |
| Put premium | FC_AMT × PREM_PUT = 1,700,000 × 0.0194 | $32,980.00 |
| Put gross at S_T = 1.04405 | FC_AMT × max(K_PUT, S_T) = 1,700,000 × 1.0990 | $1,868,300.00 |
| Put net | Gross − premium = 1,868,300 − 32,980 | $1,835,320.00 |
| Call payable at S_T = 1.15395 | FC_AMT × (min(K_CALL, S_T) + PREM_CALL) = 1,700,000 × (1.0990 + 0.0296) | $1,918,620.00 |
| Unhedged at S_T = 1.04405 | FC_AMT × S_T = 1,700,000 × 1.04405 | $1,774,885.00 |

Premiums are deducted/added at face value under the assignment convention; no financing adjustment is made. The MM hedge assumes borrowing and investing at benchmark proxies, not executable corporate rates.

## 4. Parity reconciliation

F_CIP = S0_in × (1 + R_USD × T_DAYS / 360) / (1 + R_FC × T_DAYS / 360) = 1.1052168112. Bank minus CIP = 1.1705 − 1.1052168112 = +0.0652831888 USD/EUR (652.83 pips), or $110,981.42 on the receivable. The MM result equals CIP proceeds by construction. The undated assigned quote, non-executable ECB fixing, mismatched rate benchmarks and tenor make the gap unsuitable as evidence of arbitrage. Obtain a matched executable requote.

## 5. Spec retrospective

The recovered Stage 3 audit identifies two documentation issues: the input contract was described as eleven names although it contains ten, and the original color instructions did not fully specify the four-color convention. The workbook implemented ten names and the four colors. These are documented historical findings, not numerical errors in the fresh LLM run. Another issue is the use of fixed placeholder check figures after replacing market inputs. Those tests can signal REVIEW even when the formulas remain mathematically correct. A v2 specification should distinguish invariant identities from dated regression tests and specify a separate market-parity review threshold.

The model also needs a clearer separation of receivable proceeds and hypothetical payable costs. A call must not be ranked alongside receivable hedges. The specification should state that rates are annual simple rates using ACT/360, premiums are paid upfront but treated at face value for this exercise, and the terminal spot grid uses the updated spot as its center. It should identify quote timestamps, executable versus indicative inputs, and rounding conventions. A v2 should require the model to flag missing or stale quotes rather than silently replacing them. These changes would improve reproducibility without forcing agreement with an outdated check figure. The fresh LLM explicitly identified the ten-versus-eleven input count, opposite parity sign conventions and obsolete placeholder checks. It made no observed numerical error. The specification already defines ACT/360, premium treatment and call direction correctly; preserve these provisions. The LLM assumed cash-flow certainty is the primary objective, explicitly disclosing the absence of a CFO risk tolerance. A v2 should require an explicit risk objective or conditional recommendation and a separate call sensitivity table. Standardize parity difference as implied minus quoted (-0.0652831888), with absolute magnitude for tolerance tests.

## 6. Sources and sign-off

- Stage 4 market-data memo, 2026-11-20 (source register and limitations).
- Stage 4 workbook `model(1).xlsx`, Sensitivity and Live_CIP_Audit; `model(2).xlsx`, Parity_Check (stored outputs).
- Stage 3 build audit, 2026-11-12.

Additional sources: original Stage 2 specification (2026-11-07) and user-supplied fresh-chat response, preserved in evidence.

Pending: call worksheet comparison, personal calculator verification, desktop Excel recalculation/chart inspection, external FX lab cross-check, executable bank requote and final sign-off.
