# DST scripts cron

Scheduled dispatcher for a GitHub Actions workflow.

## Workflows

- `Dispatch DST scripts update` runs every two hours and sends a
  `workflow_dispatch` event to the target workflow.
- `Keepalive` commits a timestamp once a month so scheduled workflows stay
  enabled in this repository.

## Required secret

Add a repository secret named `DST_DISPATCH_TOKEN`:

- Fine-grained personal access token scoped to the target repository.
- Permissions: `Actions: Read and write` (no contents access).
- Set an expiration and rotate it before it expires.

The token is only used to send `workflow_dispatch` events. The target workflow
handles its own repository writes.
