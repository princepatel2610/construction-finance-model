# Construction Project Cost, Cash Flow & Financial Forecasting

**Prince Patel | Excel portfolio project | In progress**

## Business question

How do changes in remaining project costs affect expected total cost, budget variance, and profitability?

This learning project explores a fictional construction and field-services business working on utility and energy projects. It connects invoice and accrual data with project forecasts, customer billings, collections, and scenario assumptions.

## What I have worked through

- Replaced direct completion-percentage references with XLOOKUP in Financial Model R9:R13 and checked a returned percentage against Project Master.
- Traced vendor invoices and accruals into actual project costs using SUMIFS.
- Reviewed commitments and the remaining-cost estimate without adding overlapping amounts twice.
- Followed calculations for expected final cost, budget variance, gross profit, and margin.
- Distinguished revenue earned, customer billings, cash receipts, receivables, and unbilled revenue.
- Reviewed the IF-based management attention flag and its limitation of showing only the first matching issue.
- Changed the scenario selector from the base case to the third scenario and compared the outputs for one project.

## Scenario finding: Substation Equipment Replacement

The figures below are fictional and in CAD. They reflect the base-case figures reviewed during the walkthrough and the third-scenario outputs observed in Excel.

| Measure | Base case | Third scenario | Change |
|---|---:|---:|---:|
| Remaining project cost | $650,000 | $728,000 | +$78,000 |
| Expected total project cost | $1,675,000 | $1,753,000 | +$78,000 |
| Contract revenue | $2,105,000 | $2,105,000 | $0 |
| Projected gross profit | $430,000 | $352,000 | -$78,000 |
| Revised cost budget | $1,620,000 | $1,620,000 | $0 |
| Budget less expected total cost | -$55,000 | -$133,000 | -$78,000 |

### Interpretation

A 12% increase in the remaining-cost forecast adds $78,000 to expected final cost. With contract revenue unchanged, projected gross profit decreases by the same amount, from $430,000 to $352,000. The project remains forecast profitable, but the expected budget overrun increases to $133,000.

### Suggested management response

Review the remaining equipment, contractor, and labour estimates to identify which costs are exposed to increases. Confirm supplier pricing and investigate options to control remaining costs. This is a recommendation for the fictional scenario, not an action taken or a measured business outcome.

## Calculation examples

```excel
Actual cost = vendor invoices + outstanding accruals for the project
Remaining cost = MAX(commitments, base estimate to complete) * (1 + scenario adjustment)
Expected total cost = actual cost + remaining cost
Cost variance = revised budget - expected total cost
Gross profit = contract revenue - expected total cost
Gross margin = IF(contract revenue=0,"n.a.",gross profit/contract revenue)
Receivables = MAX(0,client billings-cash collected)
Unbilled revenue = MAX(0,revenue recognized-client billings)
```

These are explanatory formulas. The workbook uses cell references and SUMIFS to select the relevant project and transaction type.

## Assumptions and limitations

- All project data is fictional and intended for portfolio learning. It does not represent any current or former employer's records, calculations, report formats, or materials.
- Remaining-cost estimates are assumed to include outstanding commitments. The model selects the larger of these inputs before applying a scenario adjustment; it does not add them together.
- The scenario percentage applies to the entire selected remaining-cost amount. A negative adjustment could reduce the result below recorded commitments; this simplified design needs review where commitments are fixed.
- Accruals must be cleared or reversed when the corresponding invoice is recorded. SUMIFS does not prevent double-counting automatically.
- Revenue recognized is simplified as contract revenue multiplied by an assumed completion percentage. This is not a full contract-specific revenue-recognition assessment.
- Gross profit excludes any corporate overhead, financing costs, or taxes not already included in the project cost inputs.
- MAX formulas suppress negative receivables and unbilled revenue. Excess collections and billings ahead of earnings require separate review.
- The management attention formula reports one priority issue, so an apparently lower-priority issue may not be displayed.

## Current status and next steps

The initial workbook includes a cash forecast, dashboard, and checks. My guided review has covered the principal project-level formulas and one scenario comparison. The cash forecast and full control-check walkthrough are still to be completed.

Next steps:

1. Finish the cash-flow and control-check review.
2. Write a short management summary in my own words.
3. Add a simulated month-end accounting review and invoice controls exercise.
4. Consider Power Query and Power BI after the Excel analysis is complete.

## Open the workbook

[Download the Excel workbook](Prince_Patel_Construction_Finance_Model.xlsx). On GitHub, open the file and use the download button, then open it in an Excel version that supports XLOOKUP.

The attached workbook is saved with Assumptions B6 = 2 (base case). To repeat the project P-101 scenario exercise, change B6 to 3 and review Financial Model G9, H9 and K9; restore B6 to 2 afterward. Other scenario assumptions also change, so company-level cash effects are not solely a cost sensitivity.

## XLOOKUP improvement

Financial Model R9 now uses:

```excel
=XLOOKUP($A9,'Project Master'!$A$6:$A$10,'Project Master'!$L$6:$L$10,"Check project ID")
```

The formula searches Project Master for the current Project ID and returns its completion percentage. It was copied through R13 with fixed source ranges and a changing lookup row. This improves the completion-percentage retrieval only; other fields still use positional references, so the entire model should not be described as safe to reorder independently.

[See the limited verification notes](docs/verification.md).

## Tools and contribution

Excel, XLOOKUP, SUMIFS, IF, MAX, CHOOSE, cross-sheet references, and scenario analysis.

The initial workbook and fictional dataset were generated with AI assistance. My contribution so far is a guided review of the formulas and accounting concepts, running and interpreting the scenario comparison above, and implementing the XLOOKUP change with guidance. AI also assisted with preparing this documentation. This is an ongoing learning project, not a claim of independently building or auditing the entire model.
