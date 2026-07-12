# NovaFlow Analytics: Three-Year SaaS FP&A Model (V1)

A fully formula-driven, scenario-controlled operating model for a fictional B2B SaaS company, built to portfolio standard. 36-month engine (Jan-2026 to Dec-2028), 10 sheets, ~5,200 formulas, zero hardcodes outside designated input cells.

![Executive KPI Dashboard](assets/kpi-dashboard.png)

At a glance: one dropdown flips the entire model across Base / Optimistic / Downside. The dashboard above recalculates live from the calculation spine below it: revenue and MRR roll-forwards, a formula-driven headcount and payroll build, a monthly P&L with NOL-adjusted tax, and an indirect cash flow with runway. No circular references, no hardcoded outputs.

## The business

NovaFlow Analytics sells workflow-analytics subscriptions to operations and finance teams running high-volume digital processes. Two tiers map to two segments: **Professional** (mid-market, ~$850/mo, billed monthly, inside-sales motion, higher churn) and **Enterprise** (~$4,500/mo, billed annually upfront, field-led, lower churn, expansion-driven). The plan takes ARR from ~$4m to ~$15m while EBITDA margin improves from roughly -65% to the high minus-teens, funded by an $18m Series B. Enterprise NRR runs ~106%; blended NRR approaches 100% as the Enterprise mix builds.

## Architecture

One-directional dependency spine, no circular references:

```
Scenario Manager -> Assumptions -> Revenue | Headcount | OpEx
                 -> Income Statement -> Cash Flow -> KPI Dashboard
```

- **Scenario Manager**: 10 levers x Base/Optimistic/Downside. One data-validated control cell drives a Live column via INDEX/MATCH; everything downstream reads the Live column through named ranges. Flip the dropdown and the whole model recalculates.
- **Revenue Model**: customer and MRR roll-forwards per segment (opening + new + expansion - churn), ARPU compounding at the scenario price increase, ARR growth waterfall, and a billings vs recognised-revenue split. Enterprise bills new ARR upfront and renews 1/12 of the surviving base each month; the resulting deferred revenue movement feeds the Cash Flow. This is the SaaS-specific mechanism that separates cash from P&L.
- **Headcount**: annual hiring plan by department (inputs on Assumptions), scaled by the scenario hiring pace, with salary inflation applied each January and a fully loaded factor (bonus, benefits, payroll taxes). Feeds OpEx payroll entirely by formula.
- **Operating Expenses**: COGS (hosting % of revenue + support share of Customer Success), S&M, R&D, G&A, plus a capex placeholder and straight-line depreciation that V2 replaces.
- **Income Statement**: monthly P&L with FY2026-FY2028 rollups and an NOL carryforward (tax charged only on cumulative positive pre-tax income).
- **Cash Flow**: indirect method (NI + D&A + deferred revenue movement - capex), cash roll-forward, trailing three-month burn and guarded runway. Labelled placeholder lines mean V2 working capital and financing slot in without rework.
- **KPI Dashboard**: executive cards (ARR, MRR, margins, cash, burn, runway, headcount), SaaS efficiency metrics (NRR, GRR, CAC, LTV, LTV/CAC, CAC payback, Magic Number, Rule of 40), five custom-styled charts including an ARR waterfall, and traffic-light conditional formatting.

## Conventions

Blue font on cream fill = hardcoded input. Black = formula. Green = cross-sheet link. Lookups use XLOOKUP (single-cell, non-spilling; the 2D headcount lookup nests two XLOOKUPs). MATCH appears only as a membership test in the checks panel. Negatives in parentheses, zeros as dashes. A six-line checks panel on Instructions must read all OK (scenario validity, revenue tie-out, payroll tie-out, cash tie-out, ARR waterfall tie-out, tax sign).

## Verification

The calculation engine was recalculated under all three scenarios with zero formula errors (~5,200 formulas) using an INDEX/MATCH-equivalent build; the shipped XLOOKUP formulas are a like-for-like syntax swap carrying the verified cached values, and recalculate on open in Excel (2021 or 365 required for XLOOKUP). Five formulas hand-verified against independent calculations (customer roll-forward, MRR roll-forward, billings, payroll load, depreciation). Headline outputs sense-checked: FY28 revenue $13.6m (+40%), gross margin ~84%, FY28 EBITDA margin -16% (Optimistic turns positive at +5%), CAC payback ~20 months, LTV/CAC ~5x, runway comfortable in all cases (25 months at trough in Downside).

## Roadmap

**V1 (this file)**: 10 sheets as above. **V2**: Balance Sheet, full working capital (DSO/DPO, deferred revenue balance), capex and fixed asset schedule, debt schedule and financing. The calculation spine and placeholder rows were designed so these bolt on without rework.

Fonts: Aptos Display / Aptos / Aptos Narrow / Bahnschrift SemiBold, with Arial fallbacks noted on the Instructions sheet. All figures are illustrative.

## How to use

Open `NovaFlow_Analytics_FPA_Model_v1.xlsx` in **Excel 2021 or Microsoft 365** (XLOOKUP is required; older versions and most alternative spreadsheet apps will not recalculate correctly). Start on the **Instructions** sheet for the reading guide, colour legend, and checks panel. To run a scenario, go to **Scenario Manager**, change the single control cell to Base / Optimistic / Downside, and the whole model recalculates. Blue-on-cream cells are the only inputs meant to be edited.

## What this demonstrates

An end-to-end SaaS operating model built the way a lender or investor would expect to receive it: a one-directional dependency spine with no circular references, a single scenario switch driving every downstream sheet through named ranges, SaaS-correct separation of billings, recognised revenue and deferred revenue, and a self-checking tie-out panel. It is intended as a portfolio piece showing FP&A modelling, Excel engineering, and SaaS metric fluency (NRR, GRR, CAC, LTV, CAC payback, Magic Number, Rule of 40).

## License

Released under the [MIT License](LICENSE). All figures are illustrative and for a fictional company; nothing here is financial advice.

## Author

**Soban Farid** — built as an FP&A portfolio project. Feedback and questions welcome via GitHub issues.
