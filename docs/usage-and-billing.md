# Usage and billing

Katge records tenant-scoped usage separately from credit charges. These features
are locally verified and are not enabled for production charging.

[Overview](../README.md) · [REST API](api.md) · [MCP](mcp.md) · [Release status](releases.md)

## Usage records

Usage history distinguishes inspection requests from actual metadata resolution,
cache reuse, processing attempts, successful results, failures, retries and
cancellation. Speech, visual and multimodal operations retain their outcomes.
Recorded source transfers, output sizes and server-consumed delivery bytes have
separate units and measurement descriptions.

Missing measurements are not zero usage. CPU/GPU time, provider ASR consumption,
storage duration and cloud egress costs need additional instrumentation before
they can be used for charging. Produced file size is not a cloud egress bill.

## Credits

- Versioned pricing catalogs define configurable rates; no public prices are set.
- Prepaid balances support atomic reservations and per-operation/monthly spend limits.
- A successful completed operation settles against its original catalog and hold.
- Failed processing, cancellation and partial results release the entire hold.
- Retries and repeated payment receipts cannot create duplicate charges.
- Transaction history preserves the catalog and settlement evidence.

Disabled and shadow modes do not deduct credits. An operator must explicitly
configure a tenant before credit enforcement. Statements group settled credits
by month and catalog; they are not tax invoices.

## Read APIs

All operations require the authenticated tenant's `billing:read` scope. Existing
browser-session credentials do not gain that scope automatically. REST uses its
existing OAuth audience or a scoped API key; MCP requires MCP OAuth access.

| REST GET | MCP tool | Parameters |
| --- | --- | --- |
| `/v1/billing/balance` | `katge.get_balance` | None |
| `/v1/billing/usage` | `katge.get_usage` | Optional `limit`, `before`, `period` |
| `/v1/billing/transactions` | `katge.get_billing_transactions` | Optional `limit`, `before` |
| `/v1/billing/statement` | `katge.get_billing_statement` | Required `period` |
| `/v1/usage/events` | `katge.get_usage_events` | Optional `operation_id`, `since`, `until`, `limit`, `before` |
| `/v1/usage/summary` | `katge.get_usage_summary` | Required `since`, `until` |

Credit values and usage quantities are decimal strings. Billing lists accept
`limit` 1–100 (default 50); pass the returned `next` as `before`. Operational
events accept up to 200 rows and return `next_cursor` with `occurred_at` and
`event_key`; REST accepts that cursor as URL-encoded JSON, MCP as an object.
`period` is a UTC `YYYY-MM` month. `since` and `until` are epoch milliseconds;
summary intervals may span at most 93 days and report truncation explicitly.

The public interfaces are read-only. Payment-provider verification, production
rollout, refunds, chargebacks and accounting reconciliation remain pending.
