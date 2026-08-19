<!-- markdownlint-disable -->

# Hardening Report: stoat-dev--stoat-action/v0.0.10

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **stoat-dev--stoat-action/v0.0.10** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All workflow files use mutable tag-based refs (e.g., @v2, @v3) for `uses:` steps instead of immutable 40-character SHA commit hashes. This exposes the workflows to supply-chain attacks if the referenced tags are moved or compromised. Affected references include: actions/checkout@v3, actions/setup-node@v3, actions/cache@v3, actions/upload-artifact@v3, github/codeql-action/init@v2, github/codeql-action/autobuild@v2, github/codeql-action/analyze@v2.

Locations:

- `.github/workflows/codeql-analysis.yaml:36`
- `.github/workflows/codeql-analysis.yaml:41`
- `.github/workflows/codeql-analysis.yaml:49`
- `.github/workflows/codeql-analysis.yaml:57`
- `.github/workflows/docs.yaml:22`
- `.github/workflows/docs.yaml:26`
- `.github/workflows/docs.yaml:30`
- `.github/workflows/test-action.yaml:23`
- `.github/workflows/test-action.yaml:26`
- `.github/workflows/test-action.yaml:30`
- `.github/workflows/test-action.yaml:50`
- `.github/workflows/test-cli.yaml:23`
- `.github/workflows/test-cli.yaml:26`
- `.github/workflows/test-cli.yaml:30`
- `.github/workflows/test-types.yaml:33`
- `.github/workflows/test-types.yaml:36`
- `.github/workflows/test-types.yaml:40`

### missing-permissions (severity: medium)

Four workflow files have no top-level `permissions:` key and no job-level `permissions:` key on any of their jobs. Without explicit permissions, GitHub Actions defaults to the repository's default token permissions (which may be read/write), granting more access than necessary. Each of these files should declare minimal required permissions.

Locations:

- `.github/workflows/docs.yaml:1`
- `.github/workflows/test-action.yaml:1`
- `.github/workflows/test-cli.yaml:1`
- `.github/workflows/test-types.yaml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Pinned all 7 unique action references to full 40-char SHAs with original tag preserved as inline comments. Added top-level `permissions: contents: read` to docs.yaml, test-action.yaml, test-cli.yaml, and test-types.yaml. The codeql-analysis.yaml already had job-level permissions (actions: read, contents: read, security-events: write) so no permissions change was needed there.

