<!-- markdownlint-disable -->

# Hardening Report: appleboy--jenkins-action/v1.5.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **appleboy--jenkins-action/v1.5.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in goreleaser.yml use mutable version tags instead of pinned 40-character commit SHAs, making the workflow vulnerable to supply-chain attacks if the referenced action tags are moved or compromised. Failing references: `actions/checkout@v6` (line 16), `actions/setup-go@v6` (line 20), `goreleaser/goreleaser-action@v6` (line 24).

Locations:

- `.github/workflows/goreleaser.yml:16`
- `.github/workflows/goreleaser.yml:20`
- `.github/workflows/goreleaser.yml:24`

### unpinned-uses (severity: high)

All `uses:` references in trivy.yml use mutable version tags instead of pinned 40-character commit SHAs, making the workflow vulnerable to supply-chain attacks. Failing references: `actions/checkout@v6` (line 24), `aquasecurity/trivy-action@0.33.1` (line 27), `github/codeql-action/upload-sarif@v4` (line 38), `aquasecurity/trivy-action@0.33.1` (line 43).

Locations:

- `.github/workflows/trivy.yml:24`
- `.github/workflows/trivy.yml:27`
- `.github/workflows/trivy.yml:38`
- `.github/workflows/trivy.yml:43`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all unpinned `uses:` references to full 40-character commit SHAs:

**goreleaser.yml:**
- `actions/checkout@v6` → `actions/checkout@df4cb1c069e1874edd31b4311f1884172cec0e10 # v6`
- `actions/setup-go@v6` → `actions/setup-go@924ae3a1cded613372ab5595356fb5720e22ba16 # v6`
- `goreleaser/goreleaser-action@v6` → `goreleaser/goreleaser-action@e435ccd777264be153ace6237001ef4d979d3a7a # v6`

**trivy.yml:**
- `actions/checkout@v6` → `actions/checkout@df4cb1c069e1874edd31b4311f1884172cec0e10 # v6`
- `aquasecurity/trivy-action@0.33.1` (x2) → `aquasecurity/trivy-action@b6643a29fecd7f34b3597bc6acb0a98b03d33ff8 # v0.33.1` (note: the original ref `0.33.1` was not found; resolved via `v0.33.1`)
- `github/codeql-action/upload-sarif@v4` → `github/codeql-action/upload-sarif@7188fc363630916deb702c7fdcf4e481b751f97a # v4`

