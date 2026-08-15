<!-- markdownlint-disable -->

# Hardening Report: andykenward--github-actions-cloudflare-pages/v3.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **andykenward--github-actions-cloudflare-pages/v3.3.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Two `uses:` references in codeql.yml are pinned to a mutable version tag (`@v4`) instead of a full 40-character SHA commit digest. This means the action could be silently updated to a different (potentially malicious) version without any change to the workflow file. Affected references: `github/codeql-action/init@v4` (line 27) and `github/codeql-action/analyze@v4` (line 37). These should be pinned to their full SHA, e.g. `github/codeql-action/init@<40-char-sha> # v4`.

Locations:

- `.github/workflows/codeql.yml:27`
- `.github/workflows/codeql.yml:37`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned both github/codeql-action/init@v4 and github/codeql-action/analyze@v4 in .github/workflows/codeql.yml to their full commit SHA 7188fc363630916deb702c7fdcf4e481b751f97a (the current HEAD of the v4 tag). The tag is preserved as an inline comment for readability.

