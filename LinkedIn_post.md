# LinkedIn post draft

I built a three-year SaaS operating model from scratch, and I'm putting it on GitHub for anyone to pull apart.

NovaFlow Analytics is a fictional B2B SaaS company, but the model behind it is the real work: a 36-month engine, 10 sheets, roughly 5,200 formulas, and zero hardcoded outputs. One dropdown flips the whole thing across Base, Optimistic, and Downside, and every sheet recalculates from a single scenario switch.

A few things I focused on:

- A one-directional dependency spine with no circular references. Scenario Manager feeds Assumptions, which feed Revenue, Headcount, and OpEx, which roll into the P&L, then Cash Flow, then the KPI dashboard.
- SaaS-correct mechanics: separate customer and MRR roll-forwards per segment, and a real split between billings, recognised revenue, and deferred revenue. Enterprise bills annually upfront, so cash and P&L genuinely diverge.
- A self-checking tie-out panel. Revenue, payroll, cash, and the ARR waterfall all have to reconcile before I'd call it done.
- The metrics an investor actually asks about: NRR, GRR, CAC, LTV, CAC payback, Magic Number, and Rule of 40, all live on the dashboard.

The plan takes ARR from about $4m to $15m while EBITDA margin climbs out of the deep negatives, funded by an $18m Series B. All figures are illustrative.

Repo is here: [GitHub link]

Happy to hear what you'd build differently. If you work in FP&A or SaaS finance and want to talk shop, my inbox is open.

#FPandA #SaaS #FinancialModeling #Excel #Finance #CorporateFinance
