# Financial Statement Entry Skill

A reusable Codex skill and Excel template for entering audited financial statements from audit reports into preformatted workbooks.

## What This Project Includes

- A reusable Codex skill at [skill/SKILL.md](skill/SKILL.md)
- A generic Excel template at [template/financial-statement-template.xlsx](template/financial-statement-template.xlsx)
- A simple usage example at [examples/demo-usage.md](examples/demo-usage.md)

## Intended Use Cases

- Entering consolidated and parent-company financial statements
- Working with balance sheets, income statements, and cash flow statements
- Filling supplementary-sheet items such as:
  - depreciation expense
  - amortization of intangible assets
  - amortization of long-term deferred expenses
- Verifying entry quality through rollup and reconciliation checks

## Installation

Copy the skill file to your Codex local skills directory:

```text
~/.codex/skills/financial-statement-entry/SKILL.md
```

On Windows, that is typically:

```text
C:\Users\<your-user>\.codex\skills\financial-statement-entry\SKILL.md
```

## Recommended Workflow

1. Identify the workbook structure and year columns from the Excel template.
2. Separate consolidated and parent-company statements.
3. Pull each year only from the corresponding audit report.
4. Enter only input cells and preserve formulas.
5. Reconcile key totals in the balance sheet, income statement, cash flow statement, and supplementary sheet.

## Repository Layout

```text
financial-statement-entry-skill/
├─ README.md
├─ LICENSE
├─ .gitignore
├─ skill/
│  └─ SKILL.md
├─ template/
│  └─ financial-statement-template.xlsx
└─ examples/
   └─ demo-usage.md
```

## Publishing Notes

- Before publishing, confirm you have the right to open-source the template workbook.
- Remove any client-specific information, comments, hidden sheets, personal metadata, or embedded identifiers if needed.
- If you later create a more generic public template, you can replace the current file in `template/`.

## License

This repository is released under the MIT License. See [LICENSE](LICENSE).
