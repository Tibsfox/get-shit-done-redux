---
type: Fixed
pr: 314
---
**Roadmap wave annotation now uses a planId index map** — `cmdRoadmapAnnotateDependencies` in `roadmap.cjs` was doing `planData.find(p => p.planId === planId)` inside the per-line annotation loop. Precompute a `Map<planId, planEntry>` once before the loop for O(1) lookups. Wall-time win at typical scale is negligible — this is a correctness-of-data-structure fix more than a measurable speedup.
