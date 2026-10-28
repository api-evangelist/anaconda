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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Anaconda, Inc. is the Austin, Texas company behind the Anaconda Distribution of Python and R, the conda package manager ecosystem, and the anaconda.org package repository — the default supply chain for open-source data science and AI packages. Its commercial Anaconda Platform (formerly Anaconda Cloud / Anaconda Server) adds a curated, security-scanned package repository with CVE metadata, private channels, mirroring, organization and seat management, audit logging, an on-premises repository server, Anaconda Desktop and AI Navigator for running local models and vector databases, and Agent Studio. Anaconda publishes machine-readable OpenAPI for the Anaconda Server repository API, the Organization Management API, the Audit Logs API, and the local Desktop and AI Navigator APIs, ships first-party Python client libraries and a plugin-based `anaconda` CLI, and operates conda-aware MCP servers for AI coding agents.

**Areas:** Company · Data Science · Machine Learning · Artificial Intelligence · Package Management · Python · Developer Tools · Software Supply Chain · Repository · Package Registry · Conda · MCP

## Anaconda on APIs.io

Everything profiled for Anaconda is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/anaconda/](https://apis.io/providers/anaconda/)** — or go straight to one of the APIs or properties below.

### APIs (24)

- [Anaconda.org Repository API](https://apis.io/apis/anaconda/anaconda-org-api/) — The public REST API behind anaconda.org — the community package repository that serves conda and PyPI artifacts. Exposes user/organization profiles,…
- [Anaconda MCP](https://apis.io/apis/anaconda/mcp/) — Anaconda's Model Context Protocol surface for AI coding agents. `anaconda-mcp` is a unified local gateway that composes conda-aware MCP servers, giving…
- [Anaconda Account API](https://apis.io/apis/anaconda/anaconda-account-api/) — User account actions
- [Anaconda AI Navigator API](https://apis.io/apis/anaconda/anaconda-ai-navigator-api-api/) — The AI Navigator API API from Anaconda — 1 operation(s) for ai navigator api.
- [Anaconda Artifacts API](https://apis.io/apis/anaconda/anaconda-artifacts-api/) — Artifact endpoints - search, retrieve, mirror
- [Anaconda Audit Logs API](https://apis.io/apis/anaconda/anaconda-audit-logs-api/) — The Audit Logs API from Anaconda — 5 operation(s) for audit logs.
- [Anaconda Auth API](https://apis.io/apis/anaconda/anaconda-auth-api/) — Authentication endpoints
- [Anaconda Channels API](https://apis.io/apis/anaconda/anaconda-channels-api/) — Channel management endpoints
- [Anaconda Diagnosis API](https://apis.io/apis/anaconda/anaconda-diagnosis-api/) — The diagnosis API from Anaconda — 1 operation(s) for diagnosis.
- [Anaconda Docs API](https://apis.io/apis/anaconda/anaconda-docs-api/) — The docs API from Anaconda — 1 operation(s) for docs.
- [Anaconda Files API](https://apis.io/apis/anaconda/anaconda-files-api/) — The Files API from Anaconda — 2 operation(s) for files.
- [Anaconda Groups API](https://apis.io/apis/anaconda/anaconda-groups-api/) — Group management endpoints
- [Anaconda Installers API](https://apis.io/apis/anaconda/anaconda-installers-api/) — The installers API from Anaconda — 2 operation(s) for installers.
- [Anaconda Mirrors API](https://apis.io/apis/anaconda/anaconda-mirrors-api/) — The mirrors API from Anaconda — 1 operation(s) for mirrors.
- [Anaconda Models API](https://apis.io/apis/anaconda/anaconda-models-api/) — The Models API from Anaconda — 5 operation(s) for models.
- [Anaconda Organizations API](https://apis.io/apis/anaconda/anaconda-organizations-api/) — The organizations API from Anaconda — 9 operation(s) for organizations.
- [Anaconda Repo API](https://apis.io/apis/anaconda/anaconda-repo-api/) — The Repo API from Anaconda — 2 operation(s) for repo.
- [Anaconda Reports API](https://apis.io/apis/anaconda/anaconda-reports-api/) — The reports API from Anaconda — 1 operation(s) for reports.
- [Anaconda Servers API](https://apis.io/apis/anaconda/anaconda-servers-api/) — The Servers API from Anaconda — 3 operation(s) for servers.
- [Anaconda System API](https://apis.io/apis/anaconda/anaconda-system-api/) — System endpoints - version, health, etc.
- [Anaconda Users API](https://apis.io/apis/anaconda/anaconda-users-api/) — User role management endpoints (CRUD is managed separately)
- [Anaconda Vector DB API](https://apis.io/apis/anaconda/anaconda-vectordb-api/) — The VectorDB API from Anaconda — 4 operation(s) for vectordb.
- [Anaconda Websocket API](https://apis.io/apis/anaconda/anaconda-websocket-api/) — The websocket API from Anaconda — 3 operation(s) for websocket.
- [Anaconda Cves API](https://apis.io/apis/anaconda/anaconda-cves-api/) — The cves API from Anaconda — 20 operation(s) for cves.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Anaconda Events](https://apis.io/asyncapis/anaconda/anaconda-events/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [anaconda-mcp.yml](https://apis.io/servers/anaconda/anaconda-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Anaconda Agentic Access](https://apis.io/agentic-access/anaconda/anaconda-agentic-access/)

#### Collections (22)

Postman and Open Collection request collections.

- [Anaconda Server Account API](https://apis.io/collections/anaconda/open-anaconda-account-api/)
- [AI Navigator AI Navigator API API](https://apis.io/collections/anaconda/open-anaconda-ai-navigator-api-api/)
- [Anaconda Server Artifacts API](https://apis.io/collections/anaconda/open-anaconda-artifacts-api/)
- [Audit Logs API](https://apis.io/collections/anaconda/open-anaconda-audit-logs-api/)
- [Anaconda Server Auth API](https://apis.io/collections/anaconda/open-anaconda-auth-api/)
- [Anaconda Server Channels API](https://apis.io/collections/anaconda/open-anaconda-channels-api/)
- [Anaconda Server Cves API](https://apis.io/collections/anaconda/open-anaconda-cves-api/)
- [Anaconda Server Diagnosis API](https://apis.io/collections/anaconda/open-anaconda-diagnosis-api/)
- [Anaconda Server Docs API](https://apis.io/collections/anaconda/open-anaconda-docs-api/)
- [Anaconda Files API](https://apis.io/collections/anaconda/open-anaconda-files-api/)
- [Anaconda Server Groups API](https://apis.io/collections/anaconda/open-anaconda-groups-api/)
- [Anaconda Server Installers API](https://apis.io/collections/anaconda/open-anaconda-installers-api/)
- [Anaconda Server Mirrors API](https://apis.io/collections/anaconda/open-anaconda-mirrors-api/)
- [Anaconda Models API](https://apis.io/collections/anaconda/open-anaconda-models-api/)
- [Organization Management Organizations API](https://apis.io/collections/anaconda/open-anaconda-organizations-api/)
- [Anaconda Server Repo API](https://apis.io/collections/anaconda/open-anaconda-repo-api/)
- [Anaconda Server Reports API](https://apis.io/collections/anaconda/open-anaconda-reports-api/)
- [Anaconda Servers API](https://apis.io/collections/anaconda/open-anaconda-servers-api/)
- [Anaconda Server System API](https://apis.io/collections/anaconda/open-anaconda-system-api/)
- [Anaconda Server Users API](https://apis.io/collections/anaconda/open-anaconda-users-api/)
- [AI Navigator Vector DB API](https://apis.io/collections/anaconda/open-anaconda-vectordb-api/)
- [Anaconda Server Websocket API](https://apis.io/collections/anaconda/open-anaconda-websocket-api/)

#### Overlays (5)

OpenAPI overlays, including conversational phrasing for each operation.

- [Anaconda Ai Navigator Overlay](https://apis.io/overlays/anaconda/anaconda-ai-navigator-overlay/)
- [Anaconda Audit Logs Overlay](https://apis.io/overlays/anaconda/anaconda-audit-logs-overlay/)
- [Anaconda Desktop Overlay](https://apis.io/overlays/anaconda/anaconda-desktop-overlay/)
- [Anaconda Org Management Overlay](https://apis.io/overlays/anaconda/anaconda-org-management-overlay/)
- [Anaconda Server Overlay](https://apis.io/overlays/anaconda/anaconda-server-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Anaconda Authentication](https://apis.io/security/anaconda/anaconda-authentication/)
- [Anaconda Domain Security](https://apis.io/security/anaconda/anaconda-domain-security/)
- [Anaconda Trust Center](https://apis.io/security/anaconda/anaconda-trust-center/)
- [Anaconda Vulnerability Disclosure](https://apis.io/security/anaconda/anaconda-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Anaconda Scopes](https://apis.io/scopes/anaconda/anaconda-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Anaconda Plans Pricing](https://apis.io/plans/anaconda/anaconda-plans-pricing/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.anaconda.com/)
- [Documentation](https://anaconda.com/docs/main)
- [Getting started](https://anaconda.com/docs/getting-started/main)
- [API reference](https://anaconda.com/docs/api-reference/get-api)
- [Pricing](https://www.anaconda.com/pricing)
- [Sign up](https://www.anaconda.com/app/signup)
- [Support](https://www.anaconda.com/support)
- [Blog](https://www.anaconda.com/blog)
- [Security](https://app.intigriti.com/programs/anacondainc/anacondavdp/detail)
- [Compliance](https://www.anaconda.com/security-compliance)
- [Terms of service](https://www.anaconda.com/legal/terms/terms-of-service)
- [Privacy policy](https://legal.anaconda.com/policies/en/?name=privacy-policy)
- [GitHub](https://github.com/anaconda)
- [Status](https://anaconda.statuspage.io)

## API Evangelist rating

**Kin Score 60.3** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 57.5 |
| Contract governance | 4.5 |
| Operational transparency | 34.2 |
| Developer ergonomics | 73.2 |
| Access clarity | 81.6 |

**Agent readiness 39.8** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | — |
| Event Surface Described | derived (partial credit) |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | mostly |

**Regulatory alignment 38.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/anaconda/](https://apis.io/providers/anaconda/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Anaconda: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/anaconda/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
