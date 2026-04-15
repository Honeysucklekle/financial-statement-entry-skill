# Demo Usage

## Example Prompt

```text
Please use the financial-statement-entry skill to fill the financial statement template in this folder.

Requirements:
1. Handle consolidated and parent-company statements separately.
2. Read each year only from the corresponding audit report.
3. Preserve workbook formatting and formulas.
4. Fill the supplementary sheet items if the audit report discloses:
   - depreciation expense
   - amortization of intangible assets
   - amortization of long-term deferred expenses
5. Reconcile major totals after entry and trace mismatches back to source rows.
```

## Expected Behavior

- Read the workbook structure first
- Locate statement pages in the audit reports
- Map source items to workbook rows
- Fill only input cells
- Verify rollups before completion
