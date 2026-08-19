<!-- markdownlint-disable -->

# Hardening Report: stoat-dev--stoat-action/v0.0.14

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **stoat-dev--stoat-action/v0.0.14** was hardened automatically. 9 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All uses: references in codeql-analysis.yaml use mutable tag-based refs (@v4, @v3) instead of full 40-character SHA commit hashes. Unpinned actions are vulnerable to supply-chain attacks if the tag is moved. Failing references: actions/checkout@v4, github/codeql-action/init@v3, github/codeql-action/autobuild@v3, github/codeql-action/analyze@v3.

Locations:

- `.github/workflows/codeql-analysis.yaml:35`
- `.github/workflows/codeql-analysis.yaml:40`
- `.github/workflows/codeql-analysis.yaml:46`
- `.github/workflows/codeql-analysis.yaml:57`

### unpinned-uses (severity: high)

All uses: references in docs.yaml use mutable tag-based refs (@v4) instead of full 40-character SHA commit hashes. Failing references: actions/checkout@v4, actions/setup-node@v4.

Locations:

- `.github/workflows/docs.yaml:22`
- `.github/workflows/docs.yaml:25`

### unpinned-uses (severity: high)

All uses: references in test-action.yaml use mutable tag-based refs (@v4) instead of full 40-character SHA commit hashes. Failing references: actions/checkout@v4, actions/setup-node@v4, actions/cache@v4.

Locations:

- `.github/workflows/test-action.yaml:22`
- `.github/workflows/test-action.yaml:25`
- `.github/workflows/test-action.yaml:29`

### unpinned-uses (severity: high)

All uses: references in test-cli.yaml use mutable tag-based refs (@v4) instead of full 40-character SHA commit hashes. Failing references: actions/checkout@v4, actions/setup-node@v4, actions/cache@v4.

Locations:

- `.github/workflows/test-cli.yaml:22`
- `.github/workflows/test-cli.yaml:25`
- `.github/workflows/test-cli.yaml:29`

### unpinned-uses (severity: high)

All uses: references in test-types.yaml use mutable tag-based refs (@v4) instead of full 40-character SHA commit hashes. Failing references: actions/checkout@v4, actions/setup-node@v4, actions/cache@v4.

Locations:

- `.github/workflows/test-types.yaml:30`
- `.github/workflows/test-types.yaml:33`
- `.github/workflows/test-types.yaml:37`

### missing-permissions (severity: medium)

docs.yaml has no top-level permissions: key and its only job (build) also has no job-level permissions: key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/docs.yaml:1`

### missing-permissions (severity: medium)

test-action.yaml has no top-level permissions: key and its only job (build) also has no job-level permissions: key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/test-action.yaml:1`

### missing-permissions (severity: medium)

test-cli.yaml has no top-level permissions: key and its only job (build) also has no job-level permissions: key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/test-cli.yaml:1`

### missing-permissions (severity: medium)

test-types.yaml has no top-level permissions: key and its only job (build) also has no job-level permissions: key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/test-types.yaml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all unpinned action references across 5 workflow files by replacing mutable tag-based refs with full 40-character SHA commit hashes (preserving tags as comments). Added top-level `permissions: contents: read` to docs.yaml, test-action.yaml, test-cli.yaml, and test-types.yaml. codeql-analysis.yaml already had explicit job-level permissions so no permissions fix was needed there. SHAs resolved: actions/checkout@v4=11d5960a326750d5838078e36cf38b85af677262, actions/setup-node@v4=49933ea5288caeca8642d1e84afbd3f7d6820020, actions/cache@v4=0057852bfaa89a56745cba8c7296529d2fc39830, github/codeql-action/*@v3=b7351df727350dca84cb9d725d57dcf5bc82ba26.

