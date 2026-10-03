---
name: shop-briefing
description: Give the shop owner a short status of their EsepTez shop — today's sales vs last week, what is running out, unposted drafts, debts. Use for "как дела в магазине", "дүкен қалай", morning/evening check-ins, "что заказать".
---

# Shop briefing

Uses the EsepTez MCP tools. Answer in the user's language (Kazakh or Russian), short and in plain words, numbers in ₸ with thousands separated.

1. Call `shop_health` first. It returns today's POS sales compared with the same time last week, refunds, receipts with suspicious discounts, open shifts, stock problems, unposted purchase drafts, debts and an `attention` list.
2. Lead with the main number: today's sales and the change versus last week.
3. Then only what needs action, from `attention`: items below minimum (offer `low_stock` for the list), negative stock (usually a purchase not posted), drafts waiting to be posted, discounts over the limit (offer `cashier_report`).
4. If asked "what to reorder", call `low_stock`, group by supplier if `list_suppliers` helps, and suggest quantities from recent sales (`top_items` for the last 14 days with `order_by: quantity`).
5. For a period ("за неделю", "за месяц") use `sales_report` and `top_items` with `from`/`to` (YYYY-MM-DD, Asia/Almaty days).

Do not list every number the tools return — pick the 3–5 that matter today.
