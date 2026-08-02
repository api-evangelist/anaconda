# Anaconda

Anaconda, Inc. is the Austin, Texas company behind the Anaconda Distribution of Python and R,
the conda package manager ecosystem, and the anaconda.org package repository — the default
supply chain for open-source data science and AI packages. Its commercial Anaconda Platform
adds a curated, security-scanned repository with CVE metadata, private channels, mirroring,
organization and seat management, audit logging, an on-premises repository server, Anaconda
Desktop and AI Navigator for local models and vector databases, and Agent Studio.

- Website — https://www.anaconda.com/
- Documentation — https://anaconda.com/docs/main
- Status — https://anaconda.statuspage.io
- Trust center — https://trust.anaconda.com/

## APIs

| API | Contract | Base URL |
|---|---|---|
| Anaconda Server API | OpenAPI 3.0.0 — 129 paths, 172 operations | `https://api.anaconda.cloud/api` |
| Organization Management API | OpenAPI 3.1.0 — 9 paths, 13 operations | `https://anaconda.com` |
| Audit Logs API | OpenAPI 3.1.0 — 5 paths, 5 operations | `https://anaconda.com` |
| AI Navigator API | OpenAPI 3.0.0 — 13 paths, 20 operations | local |
| Desktop API | OpenAPI 3.0.0 — 8 paths, 13 operations | local |
| Anaconda.org Repository API | no OpenAPI published | `https://api.anaconda.org` |
| Anaconda MCP | two first-party MCP servers (stdio / streamable-http) | local |

## Artifacts

`openapi/` `overlays/` `authentication/` `scopes/` `conventions/` `errors/` `lifecycle/`
`changelog/` `conformance/` `data-model/` `packages/` `cli/` `mcp/` `skills/` `llms/`
`well-known/` `security/` `asyncapi/` `agentic-access/`

Notable findings from the enrichment pass:

- Five real OpenAPI documents, four of them discovered via `https://anaconda.com/docs/llms.txt`
  and one live at `https://api.anaconda.cloud/openapi.json`.
- Verified vulnerability disclosure program (Intigriti) via RFC 9116 `security.txt`, and a
  SafeBase trust center publishing SOC 2 Type 2, ISO/IEC 27001:2022, PCI DSS, GDPR, CCPA,
  PIPEDA and VPAT.
- **No idempotency contract** anywhere in the estate, **no RFC 9457 problem+json** (three
  different vendor error envelopes instead), **no published rate limits**, **no AsyncAPI or
  webhooks**, and **no A2A agent card**.
- The AI Navigator and Desktop specifications declare **zero `operationId` values**, so their
  operations cannot be addressed by name.
