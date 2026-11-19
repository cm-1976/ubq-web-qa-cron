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

## Schedule (Europe/Rome)

| Cron UTC | Meaning (CET, UTC+1) | Role |
| --- | --- | --- |
| `30 5 * * *` | **06:30** Rome | Permanent daily |
| `0 14 * * *` | **15:00** Rome | **TEMP TEST** — remove after confirmation |

Defaults for scheduled dispatch: `ref=main`, `env=test`, `suites=all`.

In CEST (UTC+2) the wall-clock times shift +1h unless the UTC cron is adjusted.
