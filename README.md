# Katge Infrastructure

Katge extracts selected intervals from supported public video and audio.
Use the browser extension, REST API or MCP to inspect a source, choose a time
range and retrieve a clip.

[Website](https://katge.com) · [REST API](docs/api.md) · [MCP](docs/mcp.md) · [Extensions](docs/extension.md)

## Features

- MP4 and MP3 clips where supported by the source.
- Asynchronous jobs, cancellation and repeat-safe clip requests.
- Speech, visual and multimodal search previews with timestamped candidates.
- Tenant usage history, prepaid credits, spending limits and billing statements.

Search is disabled by default. Usage and billing are locally verified development
features; live payments are not enabled. Integration requires a compatible,
authorized deployment. See [release status](docs/releases.md).

## Documentation

| File | Contents |
| --- | --- |
| [docs/api.md](docs/api.md) | Clip requests, job status, results and search endpoints |
| [docs/mcp.md](docs/mcp.md) | Connection requirements and tools |
| [docs/extension.md](docs/extension.md) | Browser client and package status |
| [docs/usage-and-billing.md](docs/usage-and-billing.md) | Usage records, credits, spending limits and read APIs |
| [docs/search-openapi.json](docs/search-openapi.json) | Search and asset-extraction contract |
| [docs/privacy.md](docs/privacy.md) | Data shared with the service |
| [CHANGELOG.md](CHANGELOG.md) | Feature and documentation updates |

Katge's implementation is closed source. This repository contains public
documentation, examples and API contracts.

## Check the documentation

With Node.js 24 and Git:

```sh
node --test scripts/history.test.mjs
node scripts/check-publication.mjs
```

The checks validate documentation links, approved files and reachable Git
history. Report sensitive issues through [SECURITY.md](SECURITY.md).
