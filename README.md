# Anaconda

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
