---
name: Run a local model and vector database with Anaconda AI
description: Use the Anaconda AI Navigator / Desktop local API to browse the curated model catalog, download a model file, start and stop an inference server, and initialize a vector database with tables.
api: openapi/anaconda-ai-navigator-openapi-original.json
base_url: local — Anaconda publishes no host/port for this API
operations:
  - GET /api/models
  - GET /api/models/{id}
  - GET /models/{modelId}/files
  - PATCH /api/models/{modelId}/files/{fileId}
  - GET /api/servers
  - POST /api/servers
  - PATCH /api/servers/{serverId}
  - DELETE /api/servers/{serverId}
  - POST /api/vector-db
  - PATCH /api/vector-db
  - POST /api/vector-db/tables
  - GET /api/vector-db/tables
  - DELETE /api/vector-db/tables/{tableName}
generated: '2026-08-02'
method: generated
---

# Run a local model and vector database with Anaconda AI

> **Operations are addressed by `METHOD path`, not by name.** The AI Navigator and Desktop
> OpenAPI documents declare **no `operationId` values at all** (0 of 20 and 0 of 13). That
> is a real gap in Anaconda's specifications — do not invent ids.

## Authenticate

`Authorization: Bearer <API_KEY>` — the spec's `bearerAuth` scheme, `bearerFormat: UUID`,
described as "Enter your API key here". This is a **local** API served by Anaconda Desktop
/ AI Navigator on the developer's own machine; Anaconda publishes no host or port for it,
so resolve the base URL from the running application.

The equivalent flows are also available as CLI commands (`anaconda ai …`, see
`cli/anaconda-cli.yml`) and as MCP tools (`list_models`, `download_model`, `list_servers`,
`start_server`, `stop_server`, `remove_server`, see `mcp/anaconda-mcp.yml`).

## Steps

1. **Health check.** `GET /api/models/health` and `GET /api/servers/health` before doing
   anything else. `GET /api` returns application information.
2. **Browse the catalog.** `GET /api/models` retrieves models from the entire catalog or
   only those downloaded locally. `GET /api/models/{id}` returns metadata plus the model's
   files.
3. **Pick a file.** `GET /models/{modelId}/files` lists every file for a model;
   `GET /api/models/{modelId}/files/{fileId}` returns one file's details.
   Note the inconsistent prefix — the list operation is at `/models/...`, not `/api/models/...`.
4. **Download.** `PATCH /api/models/{modelId}/files/{fileId}` updates a model file's
   download status. This is the only download-related operation the specification
   publishes; the byte transfer itself is not a documented public operation.
5. **Start serving it.** `POST /api/servers` creates a server;
   `PATCH /api/servers/{serverId}` controls its state (start/stop);
   `GET /api/servers/{serverId}` returns its details.
6. **Stand up retrieval.** `POST /api/vector-db` initializes the vector database,
   `PATCH /api/vector-db` starts or stops it, `POST /api/vector-db/tables` creates a table,
   `GET /api/vector-db/tables` lists them, and
   `DELETE /api/vector-db/tables/{tableName}` drops one.
7. **Tear down.** `DELETE /api/servers/{serverId}` removes a server.

## Rules

- **Stop before you delete.** `DELETE /api/servers/{serverId}` returns
  **409 — "Server is currently running and cannot be deleted"**. `PATCH` it to stopped first.
- **409 on table creation** means "Table already exists" — list tables before creating.
- **404 variants**: `Model not found`, `Model or file not found`, `Server not found`,
  `Server is not running`.
- **400 variants**: `Bad request`, `Invalid action`, `Invalid request`,
  `Invalid request or database not running`. The last one means you skipped
  `POST /api/vector-db`.
- **No idempotency key.** Do not blind-retry `POST /api/servers` or
  `POST /api/vector-db/tables`; re-read with the matching list operation instead.
- The Desktop API is a strict subset of this surface — same paths minus the vector
  database (`openapi/anaconda-desktop-openapi-original.json`).
