<!-- markdownlint-disable -->

# Hardening Report: stoat-dev--stoat-action/v0.0.12

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **stoat-dev--stoat-action/v0.0.12** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple workflow files reference GitHub Actions using mutable version tags instead of immutable 40-character SHA digests, making them vulnerable to supply-chain attacks if the tag is moved.

- codeql-analysis.yaml: actions/checkout@v3, github/codeql-action/init@v2, github/codeql-action/autobuild@v2, github/codeql-action/analyze@v2
- docs.yaml: actions/checkout@v3, actions/setup-node@v3, actions/cache@v3
- test-action.yaml: actions/checkout@v3, actions/setup-node@v3, actions/cache@v3
- test-cli.yaml: actions/checkout@v3, actions/setup-node@v3, actions/cache@v3
- test-types.yaml: actions/checkout@v3, actions/setup-node@v3, actions/cache@v3

Locations:

- `.github/workflows/codeql-analysis.yaml:38`
- `.github/workflows/codeql-analysis.yaml:42`
- `.github/workflows/codeql-analysis.yaml:55`
- `.github/workflows/codeql-analysis.yaml:63`
- `.github/workflows/docs.yaml:26`
- `.github/workflows/docs.yaml:29`
- `.github/workflows/docs.yaml:33`
- `.github/workflows/test-action.yaml:24`
- `.github/workflows/test-action.yaml:27`
- `.github/workflows/test-action.yaml:30`
- `.github/workflows/test-cli.yaml:22`
- `.github/workflows/test-cli.yaml:25`
- `.github/workflows/test-cli.yaml:28`
- `.github/workflows/test-types.yaml:34`
- `.github/workflows/test-types.yaml:37`
- `.github/workflows/test-types.yaml:40`

### missing-permissions (severity: medium)

Four workflow files have no top-level `permissions:` key and no job-level `permissions:` key on any job. Without explicit permissions, workflows run with the default (potentially broad) token permissions. Each file should declare minimal required permissions.

- docs.yaml: no permissions declared
- test-action.yaml: no permissions declared
- test-cli.yaml: no permissions declared
- test-types.yaml: no permissions declared

Locations:

- `.github/workflows/docs.yaml:1`
- `.github/workflows/test-action.yaml:1`
- `.github/workflows/test-cli.yaml:1`
- `.github/workflows/test-types.yaml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Pinned all 16 unpinned action references to their immutable SHA digests across 5 workflow files (codeql-analysis.yaml, docs.yaml, test-action.yaml, test-cli.yaml, test-types.yaml). Added top-level `permissions: {}` blocks to the 4 workflow files that lacked any permissions declaration (docs.yaml, test-action.yaml, test-cli.yaml, test-types.yaml). The codeql-analysis.yaml already had job-level permissions (actions: read, contents: read, security-events: write) so no permissions block was needed there.

