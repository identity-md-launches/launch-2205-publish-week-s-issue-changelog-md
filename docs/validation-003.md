# Issue 003 validation

Validated on 19 October 2026. The publication covers **12 October 00:00 UTC through 19 October 00:00 UTC, exclusive**, the most recent complete Monday–Sunday week. Its publication date is **19 October**, not the last day covered.

Issue 003, its reporting note, the newest-first index, RSS and production export are complete. The existing application source, CSS, build configuration, package manifest, lockfile and earlier issue files are unchanged. Issue 001 already had the allowed corrected date, 10 October. The new edition is the only tab tagged Latest.

## Reporting and counting

All API requests used `CHANGELOG.md-Weekly-Research/003 (public weekly newspaper)` as their User-Agent. Research used publications, audit publications and their reports, workflows, launches, oracle requests, hourly steps, jobs and individual job details, and health. Temporary rate-limit/service errors were retried; the required collections and selected records were obtained.

The publication search examined ten pages of 100 records, including 985 within the week. The audit search examined two pages of 100, including 179 within the week. Story selection omitted spam, offensive material, duplicate projects and copies. All selected publications and attestations fall within the reporting window. No answer is general-knowledge trivia. Each story has a public API record; the watch source is embedded through `evidence/003.json`, because the specified watch schema has no source field. Visit links point to the named project sites. All five project sites returned HTTP 200 during reporting. Mnemo and Apex Run were also inspected in a browser, read-only; account actions, payments and game completion were not tested.

The lead distinguishes Mnemo's published design from privacy guarantees. Audit summaries explain possible user consequences and do not claim a live loss or a confirmed repair. The hamster answer reports the project's records, not an independently observed animal. The network-transfer answer counts transfers in the question's chosen period, not people or the entire week. Story prose contains no account addresses, hashes, programming notation, prices, market values, trading, returns or buying recommendations. Individual contributors are identified only by seat number.

| Measure | Result and method |
| --- | --- |
| Completed jobs | **2,469** completed job records with their last update inside the covered week; preceding week **3,693** |
| Launches | **292** records first created during the week and marked live when read |
| Signed answers | **890** requests with status `attested` and `attestedAt` inside the week |
| Workers online | **1,037** connected workers from `/health`, observed at **01:01:10 UTC on 19 October** |
| Weekly leaders | Seat #1814: **72**; Seat #398: **51**; Seat #1211: **44** |
| Meter | **33**: round(50 × 2,469 / 3,693), capped at 100; approximately **33% fewer completed jobs** |

The job listing was paginated to exhaustion: **14,208 records over 29 pages**, including jobs created before the week but completed or updated within it. The answer listing was also exhausted: **8,640 requests over 18 pages**. Launches returned 500 records extending into the preceding week, which covers both required boundaries. Forty-five pagination-boundary checks found no missing same-timestamp records at the checked boundaries. The saved evidence keeps relevant dated rows and the complete pagination metadata, not every unrelated historical response. `returnedCount` records each original page size; `count` describes the rows retained in the compact trail.

Individual details were read for **2,576 jobs** updated during the week, across all states. Their accepted nodes yielded **6,504 contributions with seat numbers**: 6,324 in completed jobs, 179 in blocked jobs and one in an executing job. Eighteen other accepted panel records had no seat number. They remain explicitly unattributed; no seat was guessed. Rankings use node update times and recorded seats, including accepted contributions in unfinished parent jobs. Ties use the lower seat number. These are contribution totals, not counts of distinct parent jobs. `leadersScope` is `this week`; lifetime seat totals were not used.

`/steps/hourly` returned only a rolling 24-hour series despite historical-window parameters. As in earlier issues, `numbers.accepted` therefore uses completed jobs and the interface says “Completed jobs.” It is not claimed as a weekly accepted-step count. The API is a current record, not an immutable historical snapshot: a job's last update is a proxy for completion, and an accepted node's last update is a proxy for acceptance. Missing seat attribution, later edits to records and historical completeness limit the ranking. Online is a reporting-time snapshot, not a weekly average. These definitions and the unattributed records are disclosed in the paper.

Saved trails: [`003-counts.json`](../artifacts/003-counts.json) and [`003-story-evidence.json`](../artifacts/003-story-evidence.json). The existing evidence checker independently recalculates the displayed figures from that saved trail. It reports older raw trails as unavailable; it does not falsely certify earlier reporting. The selected API claims and signatures were read, not cryptographically re-verified.

## Build and interaction results

Dependencies were installed with the existing lockfile into `/tmp/changelog-003-deps`; a disposable source mirror in `/tmp/changelog-003-build` linked that dependency directory. The repository received no dependency directory, package cache, browser download, lockfile edit or registry archive. An initial install could not write the default cache; using an explicit temporary cache resolved it.

Commands actually run:

```sh
npm ci --prefix /tmp/changelog-003-deps --cache /tmp/changelog-003-npm-cache --no-audit --no-fund
# In the disposable source mirror:
npm run typecheck
npm run build
npm run check
PLAYWRIGHT_BROWSERS_PATH=/tmp/changelog-003-browsers npm test
```

| Check | Actual result |
| --- | --- |
| TypeScript | `tsc --noEmit`, exit 0 |
| Production build | Vite 7.3.7, exit 0; three issues embedded; latest pre-rendered |
| Content and evidence | Exit 0; three schemas valid; issue 003 figures, ranking, meter and dated story trail agree |
| Browser suite | **58 checks passed**, Chromium **156.0.8078.4** |
| Accessibility automation | Zero axe violations at 1440, 1024, 768, 390 and 320px, and in the open glossary |
| Runtime errors | No application console errors or failed application resources |
| External traffic | Only Google Fonts; no API calls, external scripts, analytics or wallet requests |
| Offline | With external traffic blocked, reading and primary controls still worked; fallback fonts did not overflow |
| No JavaScript | Latest paper remained readable from the pre-rendered HTML |
| RSS and subpath | All three items newest first; issue anchors, nested static hosting and relative local URLs passed |
| Supplemental integrity | Earlier issues byte-identical; exact new schema/window; ordered index/feed; embedded JSON equals source; metadata and every selected story's dated source present |

The browser suite exercised real issue switching, arrow/Home/End keyboard navigation, hash deep links, browser Back, focus and selected states, the source switch, always-visible Visit links, native Read more/less disclosures, glossary opening/Escape/focus return, all-time versus weekly headings, date labels and the online label. It used a separate temporary archive fixture to test empty editorial sections, invalid issue links and a long scrolling tab strip. No fixture entered the real export. A supplemental production check exercised all three actual issue links, source visibility and disclosures at 390px.

The exact interaction results are in [`003-interaction-results.json`](../artifacts/003-interaction-results.json). Additional checks in [`003-render-review.json`](../artifacts/003-render-review.json) measured 390×844, 1440×1100, 320×800, 768×1024 and 1280×720. None overflowed horizontally. A separate 200% text-size check at 390px passed; this is not a native browser-zoom test.

The export was copied back after the final editorial change and tested build. Application JS and CSS retain their original hashes. The generated `dist/assets/feed-Ce2u4zBA.xml` is used by the HTML RSS-discovery link; `dist/feed.xml` is used by the footer. Both match root `feed.xml`, and both are required. No source map, dependency archive or unnecessary packaging payload is included.

## Better Interface review

The supplied guide's workflow, core principles of all six domains and design-documentation section informed the review. Its supporting accessibility, reflow, typography, writing, color and interaction guidance was applied to the new content in the existing components. The wallet reference was read; wallet functionality is outside this paper and remains absent. Implemented tokens, type, spacing, components, states and responsive behavior are documented in [`DESIGN.md`](../DESIGN.md). The supplied licenses and attribution are retained in [`design-guidance-licenses.txt`](design-guidance-licenses.txt).

| Domain | Coverage, findings and disposition |
| --- | --- |
| Accessibility | Reviewed semantic headings, landmarks, tab roles/selection, labels, switch, native dialog and disclosures in `src/App.tsx:38`, `src/App.tsx:225` and `src/App.tsx:242`. Exercised keyboard operation and focus return; axe scans passed. `src/styles.css:44` provides visible focus. Inline glossary words retain the inline-text target exception. No screen-reader session was performed. |
| Layout | Reviewed grid/column flow at `src/styles.css:84`, `src/styles.css:89`, `src/styles.css:104` and responsive rules. Inspected final mobile, desktop and glossary screenshots. No horizontal document overflow or actual lead-text collision was observed. The tab strip intentionally scrolls horizontally on phones. The probe's bounding-box overlap result is resolved below. |
| Writing | Reviewed all of `issues/003.json` and `evidence/003.json`: short explanatory reporting, specific user consequences, dated claims and explicit uncertainty. Kept source identifiers in links/evidence, out of prose. The lead is six words and its standfirst says what Mnemo does. Corrected the counting note to explicitly disclose all 18 accepted records lacking a seat. |
| Typography | Checked the implemented font stack, weights, hierarchy, line lengths and fallbacks at `src/styles.css:12`, `src/styles.css:55`, `src/styles.css:86` and `src/styles.css:116`. All three Google font families loaded; offline fallbacks and enlarged text passed. More than six sizes, four weights and compact metadata are inherited and preserved under the explicit design constraint. |
| Colors | Checked semantic tokens at `src/styles.css:3`, severity text and focus cues. Measured six opaque rendered pairs: ink/paper **14.30:1**, accent/paper **5.54:1**, muted/paper **5.49:1**, ink/panel **12.92:1**, accent/panel **5.01:1**, muted/panel **4.97:1**. Selected tabs and severity have textual/structural cues as well as color. These samples are not an exhaustive state audit. |
| UI | Exercised tabs, source switch, glossary and disclosures in `src/App.tsx:198`, `src/App.tsx:215`, `src/App.tsx:250` and `src/App.tsx:267`. Updated data flows through every section together. Sources start hidden; Visit remains visible. No added form, loading dependency, account flow, animation or storage. Required date/scope/online behavior was already implemented and is retained. |

No source-level interaction or reflow defect was found that required changing the protected visual design. The concrete fixes were editorial clarity, complete source/figure evidence and regenerated data/export; the raw probe's unresolved house-style flags are not reported as passes.

## Pinned design probe

Run from the repository root against the final export:

```sh
PLAYWRIGHT_BROWSERS_PATH=/tmp/changelog-003-browsers \
IMD_PLAYWRIGHT=/tmp/changelog-003-deps/node_modules/playwright/index.mjs \
node .imd/reads/skills/design-critic/scripts/taste.mjs --out test/scratch/taste
```

The probe ran successfully and produced **9 passing and 7 flagged checks out of 16**. Its unchanged JSON is retained as [`003-taste.json`](../artifacts/003-taste.json). Render, targets, contrast, glyphs, slogans, repetition, chrome, motion and share metadata passed. Its supplied script and scratch output are temporary task inputs, not runtime dependencies.

| Flag | Review and disposition |
| --- | --- |
| Layout | Three suspected text-box overlaps at 1440px, all inside the two-column lead (`src/styles.css:89`). A paragraph split between columns has a bounding rectangle spanning the gap and neighboring paragraph fragments. Visual inspection showed normal text flow. A DOM Range check measured **146 word fragments at each of five widths and found zero cross-paragraph word collisions**, including the inline glossary word. The raw box heuristic is retained as a false positive; no layout change was made. |
| Casing | 28 content boxes use inherited uppercase labels. Defined at `src/styles.css:56`, `src/styles.css:117`, `src/styles.css:122` and `src/styles.css:133`. |
| Tracking | 30 content boxes exceed the probe's tracking preference. The newspaper's print-style labels use the same existing rules. |
| Eyebrows | 16 detected labels above headings include masthead labels, severity badges and Visit links near following stories. Some are proximity classifications, and the actual newspaper kickers are intentional. |
| Type sizes | 14 repeated sizes per measured width, versus a house preference of six; 20/19 including one-offs. Existing styles are unchanged. |
| Type faces | Three font families and four weights, versus a house preference of three weights. The blackletter masthead and label/body font roles are preserved. |
| Copy budget | First-screen prose measured 92 words at 390 and 188 at 1440, above the probe's marketing-style limits of 60/90. This is an editorial reading product, with the inherited masthead/explainer layout. |

The task expressly requires “Keep the existing site's design, layout and code exactly as they are.” That governs the six stylistic flags. Reducing type sizes, changing tracked uppercase labels, deleting kickers or reshaping the front page would contradict that instruction. The probe also notes 20 controls below its comfortable 44px size, while its minimum-target check passes; primary tabs, switch and disclosures have 44px targets, and inline glossary words are text controls.

At **390×844**, the rendered masthead spans approximately y=108–157, issue tabs y=285–341, source switch y=343–387 and lead headline y=450–584. The product and primary controls are visible on the first screen. The latest tab is visible; older tabs remain reachable by horizontal scrolling and keyboard navigation. Title, description, favicon, `og:title` and a local 1200×630 `og:image` are present.

Screenshots inspected and retained:

- [390px first screen](../artifacts/003-screenshots/mobile-first-screen.png)
- [1440px full paper](../artifacts/003-screenshots/desktop.png)
- [Glossary dialog and close focus](../artifacts/003-screenshots/glossary.png)
- [Keyboard focus](../artifacts/003-screenshots/keyboard-focus.png)

## Limits and submission scope

WebKit was installed outside the repository, but launch failed with “Host system is missing dependencies to run browsers,” including GTK, GStreamer and ICU libraries. No Safari result is claimed. Firefox, physical devices, native screen readers, native browser zoom, forced-colors rendering and print rendering were not tested. Source rules for forced colors and print are present, but presence is not a rendered result. Automated accessibility and visual inspection do not establish complete accessibility. Site visits and audit sources do not establish third-party security.

The new `.gitignore` has an explicit path budget and exact allowlist for the nine delivered evidence files: at most **2.5 MiB JSON plus 1.25 MiB screenshots**. This permits their submission despite the existing local `artifacts/` exclusion without modifying Git configuration. All other submitted paths have the remaining **4.25 MiB** of the **8 MiB** total. Dependencies, browser downloads, caches and temporary tests remain outside that allowlist and outside the export. Complete source, lockfile and required runtime assets remain present. Final path and byte verification is recorded below.

Final packaging checks passed: **48 submission files, under 4.0 MiB uncompressed**, against the 8 MiB limit. The export is **362,210 bytes**. Evidence JSON totals **2,458,725 bytes** and the four screenshots total **1,020,622 bytes**, within their separate budgets. The complete export matches the tested build byte for byte, and both exported RSS files match the root feed. No submodules, symlinks, dependency directories, caches, source maps or dependency archives occur in the submission file set. Browser-tool scratch captures were removed; the temporary preview server was stopped. `git diff --check` and the final immutable-path comparison passed. The task's temporary input and scratch-test directories are excluded from these submission totals.
