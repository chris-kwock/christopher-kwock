# Forest Software — FX Hedging Model

This folder contains the Stage 2 design specification (`spec.md`) and Stage 3 working Excel workbook (`model.xlsx`) for Forest Software's EUR 1,700,000 receivable due in 182 days.

## Review steps

1. Open `model.xlsx` in Microsoft Excel and enable calculation.
2. Review `Cover` and `Legend_Key` for provenance and color conventions.
3. Verify the ten workbook-level named inputs using **Formulas > Name Manager**.
4. Review the forward, three-step money-market, and option formulas on their respective worksheets.
5. Check the parity and placeholder validation results on `Parity_Check`.
6. Review the eleven-scenario table and comparison chart on `Sensitivity`.
7. Change `S0_in` temporarily, confirm recalculation, then restore the initial value.

All market assumptions are indicative placeholders, not executable quotations. The EUR call calculation is a hypothetical payable hedge and must not be ranked as a receivable strategy. The upfront option premium is subtracted without financing costs under the assignment convention.

The build audit note belongs in `analysis/2026-11-12-forest-software-build-audit-analysis.md` at the repository root.
