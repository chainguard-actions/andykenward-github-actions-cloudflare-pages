<!-- markdownlint-disable -->

# Hardening Report: andykenward--github-actions-cloudflare-pages/v3.5.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **andykenward--github-actions-cloudflare-pages/v3.5.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): A ${{ ... }} expression is directly interpolated inside a run: shell command string. In the 'schema' job's 'Download GitHub GraphQL schema' step, the curl command embeds ${{ secrets.GITHUB_TOKEN }} directly in the shell script: `-H "Authorization: bearer ${{ secrets.GITHUB_TOKEN }}"`. This value flows through YAML template substitution before the shell processes it, creating a script injection risk. The safe pattern is to pass the token via an env: variable (e.g., `TOKEN: ${{ secrets.GITHUB_TOKEN }}`) and reference it as `$TOKEN` in the shell command.

Locations:

- `.github/workflows/update.yml:96`

## Iteration Notes

### Iteration 1

**Fixes applied:** script-injection

**Notes:**

Fixed script injection in .github/workflows/update.yml at line 96. Moved `${{ secrets.GITHUB_TOKEN }}` out of the `run:` shell command and into an `env:` block as `TOKEN: ${{ secrets.GITHUB_TOKEN }}`. Updated the curl command to reference `$TOKEN` as a plain environment variable instead of the direct expression interpolation.

