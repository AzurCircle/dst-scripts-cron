# DST scripts cron

Public cron dispatcher for the private
[AzurCircle/DST-scripts](https://github.com/AzurCircle/DST-scripts) mirror.

## Workflows

- `Dispatch DST scripts update` runs every two hours and calls the private
  repository's `update.yml` workflow through the GitHub API.
- `Keepalive` commits a timestamp once a month so the public repository keeps
  enough activity for scheduled workflows to stay enabled.

## Required secret

Add a repository secret named `DST_DISPATCH_TOKEN`:

- Fine-grained personal access token, resource owner `AzurCircle`.
- Repository access: only `AzurCircle/DST-scripts`.
- Permissions: `Actions: Read and write` (no contents access).
- Set an expiration and rotate it before it expires.

The token is only used to send `workflow_dispatch` events. The private
workflow runs with its own `GITHUB_TOKEN` for repository writes.
