---
name: Create a channel and manage its artifacts
description: Create an Anaconda Platform channel, inspect the artifacts it holds, resolve an artifact's dependencies and dependants, refresh the channel index, and remove an artifact.
api: openapi/anaconda-server-openapi-original.json
base_url: https://api.anaconda.cloud/api
operations:
  - repo.endpoints.channels.channels.post_channel
  - repo.endpoints.channels.channels.get_channel
  - repo.endpoints.channels.subchannels.post_subchannel
  - repo.endpoints.channels.channel_artifacts.list_artifacts
  - repo.endpoints.channels.channel_artifacts.get_artifact
  - repo.endpoints.channels.channel_artifacts.list_artifact_files
  - repo.endpoints.channels.channel_artifacts.list_artifact_dependencies
  - repo.endpoints.channels.channel_artifacts.list_artifact_dependants
  - repo.endpoints.channels.channel_artifacts.refresh_artifact_family_index
  - repo.endpoints.channels.channel_artifacts.delete_artifact
  - repo.endpoints.channels.channel_artifacts.bulk
generated: '2026-08-02'
method: generated
---

# Create a channel and manage its artifacts

## Authenticate

`Authorization: Bearer <JWT>` or `X-Auth: <user token>`. Channel creation and artifact
deletion require write permission on the channel.

## Steps

1. **Create the channel.** `repo.endpoints.channels.channels.post_channel`
   (`POST /channels`). Optionally add a subchannel with
   `repo.endpoints.channels.subchannels.post_subchannel`
   (`POST /channels/{channel_name}/subchannels`) to stage packages before promotion.
2. **Confirm it exists.** `repo.endpoints.channels.channels.get_channel`
   (`GET /channels/{channel_name}`).
3. **List what is in it.** `repo.endpoints.channels.channel_artifacts.list_artifacts`
   (`GET /channels/{channel_name}/artifacts`), paging with `offset`/`limit` and sorting
   with the artifact sort enum (`common_name`, `download_count`, `updated_at`, each with
   a `-` descending variant).
4. **Inspect one artifact.** `repo.endpoints.channels.channel_artifacts.get_artifact`
   (`GET /channels/{channel_name}/artifacts/{artifact_family}/{artifact_name}`), then
   `...list_artifact_files` for its files.
5. **Resolve the graph before you delete anything.** Call
   `repo.endpoints.channels.channel_artifacts.list_artifact_dependencies` and
   `repo.endpoints.channels.channel_artifacts.list_artifact_dependants`. Deleting an
   artifact that other packages depend on will break the channel's solvability.
6. **Delete or bulk-act.** `repo.endpoints.channels.channel_artifacts.delete_artifact`
   removes one artifact; `repo.endpoints.channels.channel_artifacts.bulk`
   (`PUT /channels/{channel_name}/artifacts/bulk`) performs a bulk action.
7. **Refresh the index.**
   `repo.endpoints.channels.channel_artifacts.refresh_artifact_family_index`
   (`PUT /channels/{channel_name}/artifacts/{artifact_family}`) after a batch of changes,
   so conda clients see a consistent repodata index.

## Rules

- **Uploads do not go through this API.**
  `repo.endpoints.channels.channel_artifacts.upload_placeholder` is explicitly documented
  as "implemented by repo-proxy, can't be called directly". Upload with
  `anaconda org upload` / `anaconda channel upload` (see `cli/anaconda-cli.yml`).
- **Do not use the deprecated copy/move operations.**
  `...channel_artifacts.move_artifact` and `...copy_artifact` are marked
  `deprecated: true` in the specification. See `lifecycle/anaconda-lifecycle.yml` for all
  24 deprecated operations.
- **Destructive steps are not idempotent and not reversible.** There is no idempotency
  key; confirm with a human before `delete_artifact` or `bulk`.
- **409 Conflict** means the resource already exists or the state transition is not
  allowed — re-read before retrying.
