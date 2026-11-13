# UBQ web QA cron (public)

Public scheduler for the private repo `cm-1976/UBQ-platform` workflow `web-qa-nightly`.

GitHub Free does **not** run `schedule` on private repositories. This public repo holds the cron; it calls `workflow_dispatch` on the private workflow.

## One-time setup

1. Create a fine-grained PAT with access to `UBQ-platform`, permission **Actions: Read and write**.
2. In this repo: Settings → Secrets and variables → Actions → New repository secret:
   - Name: `UBQ_DISPATCH_TOKEN`
   - Value: the PAT
3. Actions → **ubq-web-qa-cron** → **Run workflow** (smoke).
4. Confirm a new run appears on https://github.com/cm-1976/UBQ-platform/actions

Daily schedule: `0 10 * * *` UTC ≈ **11:00 Europe/Rome (CET)**.
