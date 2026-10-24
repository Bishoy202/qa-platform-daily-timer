# qa-platform-daily-timer

Every morning (02:23 UTC, backup 05:23 UTC) this public repo starts the `daily-refresh.yml` workflow of the
private repo `Bishoy202/Junior-QA-Platform`. GitHub does not fire scheduled workflows in that private repo (free plan),
but it does fire them here. The workflow starts nothing when a refresh already ran or is running that day.

## Setup (once)

1. Create a **fine-grained personal access token**: GitHub → Settings → Developer settings → Personal access tokens →
   Fine-grained tokens → Generate new token.
   - Repository access: **Only select repositories** → `Junior-QA-Platform`
   - Repository permissions: **Actions → Read and write** (Metadata read-only is added by itself)
2. In this repo: Settings → Secrets and variables → Actions → **New repository secret**,
   name `QA_PLATFORM_DISPATCH_TOKEN`, value = the token.
3. Test: Actions → "Start the daily job refresh" → Run workflow.

When the token expires, make a new one the same way and replace the secret.
