<!-- markdownlint-disable -->

# Hardening Report: stoat-dev--stoat-action/v0.0.13

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **stoat-dev--stoat-action/v0.0.13** was hardened automatically. 9 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/codeql-analysis.yaml are pinned to mutable tags instead of immutable 40-character SHA digests, making the workflow vulnerable to supply-chain attacks if the referenced action tags are moved. Failing references: `actions/checkout@v3` (line 38), `github/codeql-action/init@v2` (line 42), `github/codeql-action/autobuild@v2` (line 53), `github/codeql-action/analyze@v2` (line 60).

Locations:

- `.github/workflows/codeql-analysis.yaml:38`
- `.github/workflows/codeql-analysis.yaml:42`
- `.github/workflows/codeql-analysis.yaml:53`
- `.github/workflows/codeql-analysis.yaml:60`

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/docs.yaml are pinned to mutable tags instead of immutable 40-character SHA digests. Failing references: `actions/checkout@v4` (line 22), `actions/setup-node@v4` (line 25).

Locations:

- `.github/workflows/docs.yaml:22`
- `.github/workflows/docs.yaml:25`

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/test-action.yaml are pinned to mutable tags instead of immutable 40-character SHA digests. Failing references: `actions/checkout@v4` (line 22), `actions/setup-node@v4` (line 24), `actions/cache@v3` (line 27).

Locations:

- `.github/workflows/test-action.yaml:22`
- `.github/workflows/test-action.yaml:24`
- `.github/workflows/test-action.yaml:27`

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/test-cli.yaml are pinned to mutable tags instead of immutable 40-character SHA digests. Failing references: `actions/checkout@v4` (line 19), `actions/setup-node@v4` (line 21), `actions/cache@v3` (line 24).

Locations:

- `.github/workflows/test-cli.yaml:19`
- `.github/workflows/test-cli.yaml:21`
- `.github/workflows/test-cli.yaml:24`

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/test-types.yaml are pinned to mutable tags instead of immutable 40-character SHA digests. Failing references: `actions/checkout@v4` (line 30), `actions/setup-node@v4` (line 32), `actions/cache@v3` (line 35).

Locations:

- `.github/workflows/test-types.yaml:30`
- `.github/workflows/test-types.yaml:32`
- `.github/workflows/test-types.yaml:35`

### missing-permissions (severity: medium)

The workflow file docs.yaml has no top-level `permissions:` key and its only job (`build`) also has no `permissions:` key. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially write) permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/docs.yaml:1`

### missing-permissions (severity: medium)

The workflow file test-action.yaml has no top-level `permissions:` key and its only job (`build`) also has no `permissions:` key. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially write) permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/test-action.yaml:1`

### missing-permissions (severity: medium)

The workflow file test-cli.yaml has no top-level `permissions:` key and its only job (`build`) also has no `permissions:` key. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially write) permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/test-cli.yaml:1`

### missing-permissions (severity: medium)

The workflow file test-types.yaml has no top-level `permissions:` key and its only job (`build`) also has no `permissions:` key. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially write) permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/test-types.yaml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 5 workflow files in .github/workflows/:

1. codeql-analysis.yaml: Pinned actions/checkout@v3 → SHA a37ce91..., github/codeql-action/init@v2 → SHA b8d3b6e..., github/codeql-action/autobuild@v2 → SHA b8d3b6e..., github/codeql-action/analyze@v2 → SHA b8d3b6e... (already had job-level permissions, no top-level permissions needed).

2. docs.yaml: Pinned actions/checkout@v4 → SHA 11d5960..., actions/setup-node@v4 → SHA 49933ea...; added top-level `permissions: {}`.

3. test-action.yaml: Pinned actions/checkout@v4 → SHA 11d5960..., actions/setup-node@v4 → SHA 49933ea..., actions/cache@v3 → SHA 6f8efc2...; added top-level `permissions: {}`.

4. test-cli.yaml: Pinned actions/checkout@v4 → SHA 11d5960..., actions/setup-node@v4 → SHA 49933ea..., actions/cache@v3 → SHA 6f8efc2...; added top-level `permissions: {}`.

5. test-types.yaml: Pinned actions/checkout@v4 → SHA 11d5960..., actions/setup-node@v4 → SHA 49933ea..., actions/cache@v3 → SHA 6f8efc2...; added top-level `permissions: {}`.

All original tags preserved as inline comments (e.g., `# v4`) for readability.

