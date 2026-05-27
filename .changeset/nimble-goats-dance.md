---
type: Fixed
pr: 316
---
**`acquireStateLock` retry loop no longer allocates per iteration** — the lockfile-acquisition retry loop in `state.cjs` allocated a fresh `SharedArrayBuffer` + `Int32Array` on every call to `Atomics.wait`. Under contention that's measurable allocation churn for no benefit, since nothing writes to the buffer. Hoist the allocation outside the loop and reuse the same buffer across all retries.
