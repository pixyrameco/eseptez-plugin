---
name: cashier-control
description: Check how cashiers work in an EsepTez shop — discounts over the limit, free-price lines, sales below cost, refunds, night receipts, shifts. Use when the owner suspects theft or mistakes, or asks "как работают кассиры", "кассирлерді тексер".
---

# Cashier control

Uses the EsepTez MCP tool `cashier_report` (needs the "reports" permission). Answer in the user's language (Kazakh or Russian).

1. Ask for the period if it is not clear; default to the last 7 days. Call `cashier_report` with `from`/`to`.
2. Compare cashiers with each other, not with zero: refunds as % of sales, free-price lines (typed by hand without a catalog item), lines below cost and their loss, discounts over the limit or without the right, sales on credit, night receipts (23:00–07:00).
3. Point out only outliers — a cashier whose numbers are clearly higher than others — with the concrete numbers.
4. Say clearly that these are signals to check, not proof. Suggest what to look at in the dashboard: the receipts of that day, refunds approved by someone else, items sold below cost (`price_history` for that item may show a recent cost rise).

Never accuse a named person; describe what the numbers show.
