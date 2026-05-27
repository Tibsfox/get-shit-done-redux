---
type: Fixed
pr: 313
---
**Intel export extraction now uses Set-based dedupe** — the CJS and ESM export-extraction loops in `intel.cjs` were threaded with ~7 `array.includes() && array.push()` dedupe checks. Replace both `exports` and `esmExports` arrays with Sets so each lookup goes from O(n) to O(1). Insertion order is preserved (Sets iterate in insertion order), so callers that depend on declaration ordering still see the same sequence.
