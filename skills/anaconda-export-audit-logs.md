---
name: Export Anaconda audit logs
description: Query the Anaconda Platform audit trail with structured filters, then run an asynchronous bulk export job and download the resulting JSON Lines file.
api: openapi/anaconda-audit-logs-openapi-original.json
base_url: https://anaconda.com
operations:
  - get_audit_logs__get
  - get_audit_log__audit_log_id__get
  - create_export_job_export_post
  - get_export_job_status_export__job_id__get
  - download_export_export__job_id__download_get
generated: '2026-08-02'
method: generated
---

# Export Anaconda audit logs

## Authenticate

Same service-account flow as the Organization Management API:

```
POST https://anaconda.com/api/iam/token
grant_type=client_credentials&client_id=<CLIENT_ID>&client_secret=<CLIENT_SECRET>
```

Then send `Authorization: Bearer <ACCESS_TOKEN>`, `X-Org-Name: <ORG_ID>` and
`X-API-Version: v1` on every request. Tokens expire after 900 seconds — an export job can
outlive its token, so refresh before polling.

## Steps

1. **Query interactively first.** `get_audit_logs__get` (`GET /api/audit-logs`).
   - `q` is **repeatable** and structured: `column_name:value1,value2` matches entries
     whose column contains any of the listed values.
   - `search_operator` combines multiple `q` filters — `or` (default) or `and`.
   - `sort` takes `column_name` ascending or `-column_name` descending, e.g.
     `-occurred_at` for most recent first.
   - `limit` defaults to 100 and is capped at **1000**; page with `offset`.
2. **Drill into one event.** `get_audit_log__audit_log_id__get`
   (`GET /api/audit-logs/{audit_log_id}`).
3. **Start a bulk export.** `create_export_job_export_post` (`POST /api/audit-logs/export`).
   This is asynchronous — it returns a job id, not data.
4. **Poll for completion.** `get_export_job_status_export__job_id__get`
   (`GET /api/audit-logs/export/{job_id}`). Back off between polls; do not busy-loop.
5. **Download.** `download_export_export__job_id__download_get`
   (`GET /api/audit-logs/export/{job_id}/download`) once status is complete. The payload
   is **JSON Lines** — one JSON object per line, not a JSON array. Stream it; do not
   `json.load()` the whole file.

## Rules

- **Never page a full history through step 1.** Use the export job for anything beyond an
  interactive window; the list endpoint is capped at 1000 rows per call.
- **Retrying `create_export_job_export_post` creates a second job.** There is no
  idempotency key — check for an in-flight job before re-submitting.
- **422 Validation error** is the only documented failure body on this API:
  `{"detail": [{"loc", "msg", "type"}]}`. `loc` tells you which parameter was rejected.
- Audit data is compliance evidence. Anaconda's own posture (SOC 2 Type 2, ISO/IEC
  27001:2022, PCI DSS) is at `security/anaconda-trust-center.yml`; handle exported logs
  under the same controls.
