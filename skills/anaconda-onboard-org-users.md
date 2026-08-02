---
name: Onboard users into an Anaconda organization
description: Use the Anaconda Organization Management API to create a service account, add users to the organization, assign subscription seats, and issue, rotate and revoke organization access tokens.
api: openapi/anaconda-org-management-openapi-original.json
base_url: https://anaconda.com
operations:
  - create_service_account
  - list_service_accounts
  - delete_service_account
  - add_user
  - list_users
  - remove_user
  - assign_seat
  - revoke_seat
  - create_user_token
  - update_user_token
  - list_user_tokens
  - auto_register_users
generated: '2026-08-02'
method: generated
---

# Onboard users into an Anaconda organization

## Authenticate

This API is service-account only. Exchange credentials first:

```
POST https://anaconda.com/api/iam/token
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials&client_id=<CLIENT_ID>&client_secret=<CLIENT_SECRET>
```

The response carries `access_token`, `token_type: Bearer` and `expires_in: 900`.
**Tokens live 15 minutes** — refresh before long batch runs. Every subsequent request
needs three headers:

```
Authorization: Bearer <ACCESS_TOKEN>
X-Org-Name: <ORG_ID>
X-API-Version: v1
```

Some operations instead require the `Organization Admin` scheme — a bearer token minted
with `grant_type=password` from an org admin's email and password.

## Steps

1. **Create the machine identity.** `create_service_account`
   (`POST /api/v1/organizations/{org_id}/service-accounts`). The secret is returned
   **once**, on creation — store it immediately. Verify with `list_service_accounts`.
2. **Add the user.** `add_user` (`POST /api/v1/organizations/{org_id}/users`). Check the
   current roster first with `list_users`.
3. **Assign a seat.** `assign_seat`
   (`POST /api/v1/organizations/{org_id}/users/{user_id}/seats`).
4. **Issue an access token.** `create_user_token`
   (`POST /api/v1/organizations/{org_id}/users/{user_id}/token`). Set an expiry, and
   rotate it later with `update_user_token`. Audit with `list_user_tokens`.
5. **Bulk path.** `auto_register_users`
   (`POST /api/v1/organizations/{org_id}/users_auto_registration`) adds users, assigns
   seats and generates tokens in one call. Prefer it for cohort onboarding.
6. **Offboard in reverse.** `revoke_seat` → revoke the token → `remove_user`. Removing a
   user without first revoking their token leaves a live credential behind.

## Rules

- **Handle 402 explicitly.** `assign_seat` returns **402 — "No free seats remaining in
  the organization subscription"**. That is a commercial condition, not a bug: stop the
  batch and escalate to a human rather than retrying.
- **409 on `assign_seat`** means the seat is already assigned — treat as success, not an
  error.
- **404 variants matter**: `User not found`, `Service account not found`,
  `User token not found`, `A seat is not currently assigned to the user`. Read the
  `error.code`, not just the status.
- **Error envelope is nested** here: `{"error": {"code", "message", "data"}}` — different
  from the repository API's flat `{code, message, status}`. See
  `errors/anaconda-problem-types.yml`.
- **422** returns a FastAPI validation body: `{"detail": [{"loc", "msg", "type"}]}`.
- **No idempotency key exists.** Never blind-retry `create_service_account`,
  `create_user_token` or `add_user` — re-read with the matching `list_*` operation first.

## Verify afterwards

Confirm the change landed in the audit trail with the Audit Logs API
(`get_audit_logs__get`, `GET /api/audit-logs`) filtered with
`q=column_name:value` and sorted `-occurred_at`.
