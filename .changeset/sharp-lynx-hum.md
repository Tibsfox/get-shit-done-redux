---
type: Fixed
pr: 305
---
**Statusline todo lookup now does a single-pass scan** — replaces a `.filter().map(statSync).sort()` chain in `hooks/gsd-statusline.js` with a single-pass walk that keeps only the newest matching session-todos file. Same syscall count; intermediate arrays and the unnecessary sort are gone.
