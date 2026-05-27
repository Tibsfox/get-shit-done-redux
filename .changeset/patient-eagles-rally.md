---
type: Fixed
pr: 319
---
**Diff-only lint workflows use shallow checkout** — `docs-required.yml` and `changeset-required.yml` both used `fetch-depth: 0` (full history) when their lint scripts only need the three-dot diff against the base ref. Switch to `fetch-depth: 50` plus an explicit base-ref fetch — enough history to cover the merge-base for >99% of realistic PRs, dramatically faster than the full clone.
