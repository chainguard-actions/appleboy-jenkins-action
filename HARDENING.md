<!-- markdownlint-disable -->

# Hardening Report: appleboy--jenkins-action/v1.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **appleboy--jenkins-action/v1.3.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All uses: references in goreleaser.yml use version tags instead of full 40-character SHA commit hashes, making the workflow vulnerable to supply-chain attacks if the referenced tags are moved or overwritten. Failing references: actions/checkout@v6, actions/setup-go@v6, goreleaser/goreleaser-action@v6.

Locations:

- `.github/workflows/goreleaser.yml:14`
- `.github/workflows/goreleaser.yml:19`
- `.github/workflows/goreleaser.yml:24`

### unpinned-uses (severity: high)

All uses: references in trivy.yml use version tags or version strings instead of full 40-character SHA commit hashes, making the workflow vulnerable to supply-chain attacks. Failing references: actions/checkout@v6, aquasecurity/trivy-action@0.33.1 (used twice), github/codeql-action/upload-sarif@v4.

Locations:

- `.github/workflows/trivy.yml:22`
- `.github/workflows/trivy.yml:26`
- `.github/workflows/trivy.yml:38`
- `.github/workflows/trivy.yml:44`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all unpinned action references to full 40-character SHA commit hashes in both workflow files:

**goreleaser.yml:**
- actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803 # v6
- actions/setup-go@v6 → @924ae3a1cded613372ab5595356fb5720e22ba16 # v6
- goreleaser/goreleaser-action@v6 → @e435ccd777264be153ace6237001ef4d979d3a7a # v6

**trivy.yml:**
- actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803 # v6
- aquasecurity/trivy-action@0.33.1 → @b6643a29fecd7f34b3597bc6acb0a98b03d33ff8 # 0.33.1 (SHA resolved from v0.33.1 tag, as the tag without 'v' prefix does not exist in the repo)
- github/codeql-action/upload-sarif@v4 → @e0647621c2984b5ed2f768cb892365bf2a616ad1 # v4

Original tag names are preserved as inline comments for readability.

