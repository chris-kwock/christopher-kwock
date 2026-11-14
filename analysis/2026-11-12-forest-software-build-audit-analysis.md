# Stage 3 Build Audit — Forest Software

**Auditor:** Christopher Kwock
**Date:** 2026-11-12  
**Artifact:** `capabilities/fx-hedging/model.xlsx`  
**Status:** Automated structural and formula checks completed; manual Excel inspection remains required.

## Audit approach

Generated the workbook from the Stage 2 Forest Software specification and checked the named input ranges, core hedge formulas, visible validation outputs, and sensitivity chart. These findings describe checks actually performed during workbook generation; the student should independently inspect the file in Excel and update this record.

## Finding 1 — Named-range contract: confirmed

**Checked:** Workbook-level named ranges and their destinations.  
**Found:** Exactly ten input names (`FC_AMT`, `S0_in`, `F0_in`, `R_USD`, `R_FC`, `K_PUT`, `K_CALL`, `PREM_PUT`, `PREM_CALL`, `T_DAYS`) all point to the intended `Inputs!B6:B15` cells. The Stage 2 narrative had incorrectly called the contract eleven inputs in some places even though its table lists ten.  
**Action:** Built ten named ranges matching the official contract. **Spec fix required:** change any 'eleven' references to 'ten' before committing the revised spec.

## Finding 2 — Color convention: gap identified and corrected in build

**Checked:** Build contract against Stage 2 color instructions.  
**Found:** Stage 3 explicitly requires Yellow = inputs, Blue = assumptions, Green = formulas, Gray = outputs, while the earlier Stage 2 draft primarily described yellow and gray.  
**Action:** Implemented all four fills in the workbook and added a dedicated `Legend_Key` worksheet. **Spec fix required:** revise the Stage 2 spec to explicitly require the four-color convention.

## Finding 3 — Calculation check figures: confirmed

**Checked:** Formula-derived outputs and independent arithmetic.  
**Found:** Forward $1,989,850.00; money market $1,989,847.99; put floor $1,956,020.00; call maximum payable cost $2,039,320.00. The visible parity status and eight additional validation cells show PASS with the original illustrative inputs.  
**Action:** Retained unrounded calculations and visible tests on `Parity_Check`. No numerical correction was necessary.

## Finding 4 — Sensitivity and chart: structurally confirmed

**Checked:** Formula expressions in the eleven sensitivity rows and presence of a line chart.  
**Found:** Eleven formula-driven spot scenarios from -5% through +5%; forward and money-market values remain fixed, unhedged proceeds increase with the spot rate, and put proceeds have a floor. One chart is anchored on the Sensitivity tab.  
**Action:** Kept formulas linked to `S0_in`, `FC_AMT`, the option parameters, and hedge calculations. **Manual check still required:** change `S0_in` in Excel, verify recalc and chart movement, then restore the input.

## Finding 5 — Check-figure tolerance behavior: disclosed limitation

**Checked:** Whether the validation rules distinguish placeholder checks from universal identities.  
**Found:** Fixed check figures will correctly show REVIEW after changing the placeholder assumptions, even if the new scenario is internally consistent. The parity checks likewise use illustrative tolerances, not executable-market arbitrage bounds.  
**Action:** Added an explicit warning to `Parity_Check`. In Stage 4, update benchmark-specific check figures and explain any differences caused by real borrowing/lending spreads.

## Outstanding manual audit before GitHub submission

Open `model.xlsx` in desktop Excel; confirm the named ranges using **Formulas > Name Manager**; click sample calculated cells to confirm they contain formulas; change `Inputs!B7` (`S0_in`) temporarily and verify that the sensitivity table and chart move; restore `1.1700`; confirm the visible PASS results; inspect the chart and formatting; then upload the file to the specified GitHub path. No claim is made that these manual steps have already been performed.
