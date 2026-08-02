---
name: Audit an Anaconda channel for CVEs
description: Enumerate the vulnerabilities affecting packages in an Anaconda Platform channel, drill into a specific CVE, and identify exactly which package files are affected so remediation can be scoped.
api: openapi/anaconda-server-openapi-original.json
base_url: https://api.anaconda.cloud/api
operations:
  - repo.endpoints.channels.channels.list_channels
  - repo.endpoints.channels.channel_artifacts.list_channel_cves
  - repo.endpoints.channels.channel_artifacts.get_channel_cve_details
  - repo.endpoints.channels.channel_artifacts.list_channel_cve_files
  - repo.endpoints.channels.channel_artifacts.list_artifact_cves
  - repo.endpoints.channels.channels_cve_history.get_cve_channel_history
generated: '2026-08-02'
method: generated
---

# Audit an Anaconda channel for CVEs

Anaconda's commercial value in the repository API is CVE metadata attached to curated
packages. This skill walks a channel from "which channels can I see" down to "which
files must be replaced".

## Authenticate

Send a JWT bearer token, or a long-lived user token in the `X-Auth` header:

```
Authorization: Bearer <JWT>
# or
X-Auth: <user token>
```

A 401 means no token or an invalid token; a 403 means the token is valid but lacks
access to that channel. See `authentication/anaconda-authentication.yml`.

## Steps

1. **Find the channel.** Call `repo.endpoints.channels.channels.list_channels`
   (`GET /channels`). Use `offset` / `limit` (defaults 0 / 100) to page, `q` to search,
   and `sort` with the channel sort enum. Prefer
   `repo.endpoints.channels.channels.list_my_channels` (`GET /account/channels`) when
   you only need channels the caller can already access.
2. **List the channel's CVEs.** Call
   `repo.endpoints.channels.channel_artifacts.list_channel_cves`
   (`GET /channels/{channel_name}/cves`). Narrow with `cve_status`, `min_cve_score`
   and `max_cve_score` rather than filtering client-side — the result sets are large.
3. **Get CVE detail.** Call
   `repo.endpoints.channels.channel_artifacts.get_channel_cve_details`
   (`GET /channels/{channel_name}/cves/{cve_id}`).
4. **Scope the blast radius.** Call
   `repo.endpoints.channels.channel_artifacts.list_channel_cve_files`
   (`GET /channels/{channel_name}/cves/{cve_id}/files`) to get every package file in
   the channel carrying that CVE.
5. **Check a single package instead.** When you already know the package, call
   `repo.endpoints.channels.channel_artifacts.list_artifact_cves`
   (`GET /channels/{channel_name}/artifacts/{artifact_family}/{artifact_name}/cves`).
   `artifact_family` is the package ecosystem (for example `conda`, `python`).
6. **Show the trend.** Call
   `repo.endpoints.channels.channels_cve_history.get_cve_channel_history`
   (`GET /channels/{channel_name}/cves_history`) for the channel's CVE history log.

## Rules

- **Paginate.** Every list operation is offset/limit with a `{total_count, items}`
  envelope. Never assume the first page is the whole set.
- **Subchannels are a parallel tree.** If the channel has subchannels, repeat step 2
  against `repo.endpoints.channels.subchannel_artifacts.list_subchannel_cves`; CVEs on
  a subchannel are not returned by the channel-level call.
- **There is a streaming variant.** `GET /channels/{channel_name}/cves/ws`
  (`repo.endpoints.channels.channel_artifacts.cve_report_batched`) is a WebSocket that
  batches a full CVE report. Use it for whole-channel reporting instead of paging the
  REST endpoint thousands of times.
- **No retries on writes.** Anaconda publishes no idempotency key, so never blindly
  retry a non-GET. See `conventions/anaconda-conventions.yml`.
- **Errors** are `{code, message, status}`, not RFC 9457 problem+json. See
  `errors/anaconda-problem-types.yml`.
