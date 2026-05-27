---
type: Fixed
pr: 307
---
**Phase dependency traversal is now O(V+E) instead of O(V*(V+E))** — Kahn's-algorithm BFS in `get-shit-done/bin/lib/phase.cjs` was using `Array.shift()` for queue dequeue, causing per-call O(n) reindex cost. Behavior is unchanged (same dequeue order, same cycle detection); only the asymptotic complexity improves for larger phase graphs.
