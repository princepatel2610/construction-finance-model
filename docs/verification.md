# Verification notes

Review date: October 3, 2026 (Regina)

The uploaded workbook was inspected without modifying it. The workbook in this package is byte-for-byte identical to that upload.

## XLOOKUP checks

- All five formulas in Financial Model R9:R13 use the expected changing Project ID row and fixed search/return ranges.
- The saved results match the corresponding Project Master completion percentages.

| Cell | Project | Saved completion | Comparison |
|---|---|---:|---|
| R9 | P-101 | 65% | Match |
| R10 | P-102 | 72% | Match |
| R11 | P-103 | 58% | Match |
| R12 | P-104 | 83% | Match |
| R13 | P-105 | 49% | Match |

## Other observations

- Assumptions B6 is saved as 2, with a 0% remaining-cost adjustment.
- Saved P-101 base-case outputs are G9 $650,000, H9 $1,675,000, K9 $430,000.
- No stored Excel error cells were found across the eight sheets.
- No external workbook link parts were found.

## Review limits

This was a formula and saved-value inspection, not a new live Excel recalculation, comprehensive model audit, visual review, or proof that every scenario and control is correct. Prince previously reported running the third scenario in Excel and matching one copied XLOOKUP result to Project Master. Further cash-flow and control walkthroughs remain planned.

Workbook SHA-256: `df81d686f28455111f505a5004025aa7e7aef89e74b61fd114d960b0f74dc5f1`
