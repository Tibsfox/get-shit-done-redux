---
type: Fixed
pr: 311
---
**Sub-repo routing now uses a first-segment bucket index** — `cmdCommitToSubrepo` in `commands.cjs` was doing `subRepos.find(file.startsWith(repo + '/'))` inside the per-file loop, an O(F*R) shape. Adds a first-segment bucket Map so most files land directly in the right candidate list. Multi-segment sub-repos (e.g. `vendor/pkg`) still resolve via the inner `startsWith` fallback. Behavior is identical for all valid inputs.
