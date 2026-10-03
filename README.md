# EsepTez plugin

Your [EsepTez](https://www.eseptez.kz) shop inside an AI assistant: today's sales, what is running out, who owes money, how cashiers work — and a goods receipt from a photo of a supplier invoice.

The plugin connects the EsepTez MCP server `https://www.eseptez.kz/api/mcp` (sign-in through EsepTez, OAuth) and adds three skills:

| Skill | What it does |
|---|---|
| `invoice-to-purchase` | Photo of a supplier invoice → matched items, price check, **draft** goods receipt |
| `shop-briefing` | Sales vs last week, items running out, unposted drafts, debts |
| `cashier-control` | Discounts over the limit, free-price lines, sales below cost, refunds by cashier |

Writes are drafts only: stock and debts change after a person posts the draft in the dashboard.

## Install

**Claude Code**

```
/plugin marketplace add pixyrameco/eseptez-plugin
/plugin install eseptez@eseptez
```

**Claude (web, desktop, phone)** — without the plugin: Settings → Connectors → Add custom connector → `https://www.eseptez.kz/api/mcp`.

**ChatGPT** — on chatgpt.com (computer): Settings → Security and login → Developer mode, then Plugins → «+» → `https://www.eseptez.kz/api/mcp`. On Plus and Pro ChatGPT allows read-only tools, so goods receipts from photos need Claude or a ChatGPT Business/Enterprise workspace.

## Layout

```
plugin.json              portable manifest (agent-plugins.org) + ChatGPT presentation (extensions.com.openai)
mcp.json                 MCP server, agent-plugins.org format
.claude-plugin/          Claude Code manifest and marketplace (this repo is the marketplace)
.mcp.json                MCP server, Claude Code format
skills/*/SKILL.md        skills, shared by both
assets/                  icon and logo
```

Docs and examples: https://www.eseptez.kz/ai · Privacy: https://www.eseptez.kz/privacy
