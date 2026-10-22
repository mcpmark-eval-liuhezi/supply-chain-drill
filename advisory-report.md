# Supply-chain security drill

Reproducible end-to-end drill executed ahead of the team sync. One real, currently listed advisory from GitHub's public advisory database was selected, drill artifacts were built around it, and a remediation pass was performed. Repo: `mcpmark-eval-liuhezi/supply-chain-drill`.

## Advisory under test

| Field | Value |
| --- | --- |
| **GHSA ID** | GHSA-673q-mjm6-r5xr |
| **CVE** | No CVE assigned |
| **Severity** | Critical |
| **Affected package** | `next` (npm — the Next.js framework, vercel/next.js) |
| **Vulnerable version range** | >= 16.0.0, <= 16.4.0 |
| **Earliest patched version** | 16.4.1 |
| **Advisory link** | https://github.com/advisories/GHSA-673q-mjm6-r5xr |

**Advisory summary:** Unauthenticated Remote Code Execution in `use cache` functions returning typed arrays. A vulnerability in applications using the App router with Cache Component can lead to remote code execution when the application has a `use cache` function that returns multiple typed arrays. There is no known workaround for affected applications with such functions — upgrade immediately, even if the application does not have similar functions. CWE-502 (Deserialization of Untrusted Data). Found by @evolutionstorm; published 2026-10-22.

## Notification check

The unread-notifications review could not be completed as planned: the GitHub API rejected the notifications query with `403 Resource not accessible by personal access token`, on both the default and participating-only filters. In other words, the access token in use is not scoped to read the account's notifications, so no unread security- or pull-request-related notifications could be opened or folded into this write-up. **No unread notifications could be reviewed; none were found or actioned via this drill.** Recommendation: re-run the notification check with a token that includes the `notifications` scope before the team sync.

## Actions taken

1. **Advisory selection** — Selected a currently listed, GitHub-reviewed advisory rated **critical** affecting an npm package: GHSA-673q-mjm6-r5xr (`next`), and pulled its full record (GHSA ID, CVE status, severity, affected package, vulnerable range, earliest patched version).
2. **Repository created** — `supply-chain-drill`, initialized with a README. Note: the token in use cannot create repositories on the personal account, so the repo was created in the accessible organization `mcpmark-eval-liuhezi`.
3. **Branch created** — `drill/advisory-writeup`, off the default branch (`main`).
4. **Simulated vulnerable manifest added to `main`** — `package.sample.json`, scaffolding only, referencing `next` at `16.4.0`, which falls inside the advisory's vulnerable range (>= 16.0.0, <= 16.4.0).
5. **Drill write-up committed** — this file, `advisory-report.md`, on `drill/advisory-writeup`.
6. **Pull request opened** — "Security drill: advisory writeup", from `drill/advisory-writeup` into `main`, with the advisory summary in its description.
7. **Tracking issue opened** — "Advisory drill follow-up", referencing GHSA-673q-mjm6-r5xr, labeled `security-drill` (issue type: Task).
8. **Copilot automated code review requested** on the pull request.
9. **Remediation simulated** — deleted `package.sample.json` from the default branch (`main`), as the simulated fix.
10. **Issue comment recorded** — left a short comment on the tracking issue noting that the manifest was removed from `main`.
