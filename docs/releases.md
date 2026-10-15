# Release status

Updated 15 October 2026. This page describes development status, not a service
deployment or browser-store release.

| Feature | Status |
| --- | --- |
| Clip REST API and MCP | Implemented; a compatible authorized deployment is required |
| Browser extension 1.1.0 | Unpublished candidate; service and target-browser acceptance remain |
| Speech, visual and multimodal search | Optional preview, disabled by default |
| Usage history and prepaid-credit billing | Locally verified; production rollout and payment integration remain |

The latest local candidate passed 75 focused regression tests, TypeScript,
build and lint checks. A separate real PostgreSQL test verified concurrent
credit reservations, settlement and payment-receipt replay. These checks do not
establish live provider availability, browser-store acceptance or production
payment readiness.

Search results remain candidates with coverage and partial status. Turkish
visual-query quality and reliable detection of every short event are not
established. Live payments remain disabled, and no public prices are assigned.

See [usage and billing](usage-and-billing.md), [API](api.md), [MCP](mcp.md)
and the [changelog](../CHANGELOG.md).
