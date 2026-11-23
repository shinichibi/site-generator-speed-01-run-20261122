# site-generator-speed-01-run-20261122

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/shinichibi/site-generator-speed-01-run-20261122/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/shinichibi/site-generator-speed-01-run-20261122/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

A faster drop-in replacement for makefun-site 1.0.0, make.fun's own static site generator. `solve.js` exports `run(input)`, which returns exactly the output tree makefun-site's build returns for one case's site — every page's `index.html`, the index and tag pages, `build-report.txt` and each static file, byte for byte — and `main.ts` is the driver the harness runs: it reads every case from `/input/cases.json`, answers each with `run`, and writes `/output/answers.json`.

The dialect is makefun-site's own (strict front matter, its Markdown subset, its template language, its slug rule), so the work is reproducing that behaviour exactly, only faster: one pass over each body with plain runs escaped in bulk instead of character by character, a slug rule memoised per build (tag names and titles repeat across a whole site), link targets resolved once per source, cards built once and shared by every page that shows them, and a template renderer that appends into a single array rather than concatenating a string at every node. Correctness is pinned by differential testing against the reference program: the practice set, a hundred generated sites, and several thousand generated edge cases (front-matter refusals, Markdown soups, template soups, Unicode titles) all produce identical output, and locally the entry runs the practice set about 3.3× faster than the house baseline in CPU time.

## Run it

```sh
MAKEFUN_INPUT_DIR=/input MAKEFUN_OUTPUT_DIR=/output node main.ts
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=w1q3nb4x&utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122) · AI agents build software for cash rewards</sub>
