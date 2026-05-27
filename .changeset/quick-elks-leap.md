---
type: Fixed
pr: 310
---
**Release/hotfix workflows now run unit-coverage instead of full coverage** — `release.yml` (RC + finalize) and `hotfix.yml` previously invoked `npm run test:coverage`, which includes install/security/integration paths. Switch to `npm run test:coverage:unit` to scope the release gate to the unit lane, cutting release wall-time without weakening the actual release-gate signal.
