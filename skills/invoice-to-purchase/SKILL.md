---
name: invoice-to-purchase
description: Turn a photo or file of a supplier invoice (накладная / жүкқұжат) into a draft goods receipt in EsepTez. Use when the user sends an invoice picture, says "сделай приход", "кіріс жаса", or asks to add delivered goods to stock.
---

# Supplier invoice → draft goods receipt

The EsepTez MCP server must be connected (tools `search_items`, `compare_invoice_prices`, `list_suppliers`, `create_purchase_draft`). Answer in the user's language (Kazakh or Russian). Money is KZT (₸).

1. **Read the invoice.** Extract supplier name, invoice number and date, and every line: name as printed, barcode if printed, quantity, unit, purchase price per unit. If a line shows only a line total, divide by quantity. Say which lines you could not read instead of guessing.
2. **Find the supplier** with `list_suppliers` (match by name). If none matches, you will pass `supplier_name` and EsepTez creates it.
3. **Match every line** with one `search_items` call using `queries` (barcode when printed, otherwise the name). Prefer an exact barcode match. If several items match a name, pick the one with the same volume/weight; if still unsure, ask the user. Lines with no match become new items.
4. **Check prices** with `compare_invoice_prices` for the matched lines (pass `supplier_id` if known, `quantity` for each line). Tell the user briefly about `price_up` lines (old → new price, %), lines `at_or_above_retail`, and the extra cost versus last prices.
5. **Confirm** the summary with the user: supplier, number of lines, total, new items to be created, price rises.
6. **Create the draft** with one `create_purchase_draft` call: matched lines as `item_id`, unmatched as `new_item` (name, unit as on the invoice, barcode if printed, category if obvious), `doc_number`, `doc_date`, `paid` only if the user says it was paid.
7. **Give the link** from the response and remind: the draft is not posted — stock and supplier debt change only after a person checks it in the dashboard and presses «Провести / Өткізу».

Never post or delete documents, never invent barcodes, and never change retail prices unless the user asks (`sell_price`).
