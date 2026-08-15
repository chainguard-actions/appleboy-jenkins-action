<!-- markdownlint-disable -->

# Hardening Report: appleboy--jenkins-action/v1.4.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **appleboy--jenkins-action/v1.4.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in the workflow files are pinned to mutable tags or version strings rather than immutable 40-character SHA digests. This exposes the action to supply-chain attacks where a tag is silently moved to a different (potentially malicious) commit.

Failing references in goreleaser.yml:
- `uses: actions/checkout@v6`
- `uses: actions/setup-go@v6`
- `uses: goreleaser/goreleaser-action@v6`

Failing references in trivy.yml:
- `uses: actions/checkout@v6`
- `uses: aquasecurity/trivy-action@0.33.1`
- `uses: github/codeql-action/upload-sarif@v4`
- `uses: aquasecurity/trivy-action@0.33.1`

Each should be pinned to a full 40-character commit SHA, e.g. `uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/goreleaser.yml:14`
- `.github/workflows/goreleaser.yml:19`
- `.github/workflows/goreleaser.yml:23`
- `.github/workflows/trivy.yml:22`
- `.github/workflows/trivy.yml:26`
- `.github/workflows/trivy.yml:36`
- `.github/workflows/trivy.yml:44`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 7 unpinned `uses:` references to full commit SHAs:

**goreleaser.yml:**
- `actions/checkout@v6` → `@df4cb1c069e1874edd31b4311f1884172cec0e10 # v6`
- `actions/setup-go@v6` → `@924ae3a1cded613372ab5595356fb5720e22ba16 # v6`
- `goreleaser/goreleaser-action@v6` → `@e435ccd777264be153ace6237001ef4d979d3a7a # v6`

**trivy.yml:**
- `actions/checkout@v6` → `@df4cb1c069e1874edd31b4311f1884172cec0e10 # v6`
- `aquasecurity/trivy-action@0.33.1` (×2) → `@b6643a29fecd7f34b3597bc6acb0a98b03d33ff8 # v0.33.1` (note: the tag `0.33.1` without `v` prefix was not found; resolved via `v0.33.1`)
- `github/codeql-action/upload-sarif@v4` → `@7188fc363630916deb702c7fdcf4e481b751f97a # v4`

