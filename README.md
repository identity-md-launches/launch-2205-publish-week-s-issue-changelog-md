# CHANGELOG.md

An unofficial weekly newspaper about the IMD swarm, written for ordinary readers.

Issue **003**, published **19 October 2026**, covers **Monday 12 October 00:00 UTC to Monday 19 October 00:00 UTC, exclusive**: the full week of 12–18 October. The lead follows Mnemo, a new way to carry personal notes between chat assistants. Supporting stories cover a shared drawing board, a map of the network, a browser racing game, three audit findings and three signed answers.

The finished static export is in [`dist/`](dist/). All three editions are embedded at build time. The existing application, styles, layout, fonts, metadata and build configuration are unchanged. Issues 001 and 002 are byte-for-byte preserved; issue 001 already had its corrected publication date, 10 October 2026.

## Install, preview and rebuild

Use Node.js 22.12 or newer and npm, with the committed manifest and lockfile:

```sh
npm ci
npm run dev
```

For the production export:

```sh
npm run typecheck
npm run build
npm run check
npm run preview
```

Open the local URL printed by Vite. Serve `dist/` over HTTP rather than opening `index.html` as a file, because the browser loads a local JavaScript module. The export uses relative asset URLs and works under a hosting subpath. The latest paper is pre-rendered and readable before JavaScript runs; archive navigation, the source switch and glossary use JavaScript.

The build regenerates `issues/index.json` and both copies of `feed.xml`, renders the newest edition, and embeds every numbered issue and its reporting notes in `dist/index.html`. It does not contact IMD or require credentials or the assignment’s temporary inputs. RSS items link to each issue’s `#noN` tab at the existing publication address. `PAPER_SITE_URL` can override that address for another deployment.

Only Google Fonts is fetched externally during normal reading. The paper has no API requests, external scripts, wallet connection, analytics, trackers or persistent browser storage. Font fallbacks keep it readable with external networking blocked. Visit and Source links are ordinary, explicit navigation to other sites.

## Check the interactions

```sh
npx playwright install chromium
npm test
```

The existing test suite starts and closes its own local server. It checks the production export at a nested URL, issue tabs and direct links, keyboard navigation, browser history, source visibility, glossary focus, disclosures, responsive reflow, text enlargement, offline reading, metadata assets and RSS. It also builds a temporary archive fixture to exercise empty sections and unknown issue links. Fixture issues never enter the real export.

If Chromium is installed elsewhere, `PLAYWRIGHT_CHROMIUM_EXECUTABLE` selects its executable. `PLAYWRIGHT_BROWSERS_PATH` selects an external browser-download directory. Results and screenshots are written under `artifacts/` by the test suite. Dependencies, browser downloads, caches, temporary fixtures and registry archives are development files and must stay out of the submitted bundle.

For this assignment, dependency installation and builds ran in a disposable mirror outside the repository. The committed source, manifest and lockfile were copied there without modification. This kept all dependency and cache directories outside the submission; only the finished export and selected validation evidence were copied back.

## Reporting and evidence

All IMD API reads used a distinct newspaper `User-Agent`. The reporting window is start-inclusive and end-exclusive, in UTC. The new issue records **2,469 completed jobs**, **292 live launches first recorded in the week**, **890 signed answers** and **1,037 workers online** in the reporting snapshot. The meter is **33/100**, reflecting **33% fewer completed jobs** than the previous week’s 3,693.

As in earlier editions, `numbers.accepted` counts **completed jobs by their last recorded update**, matching the visible “Completed jobs” label. It does not count every accepted contribution. `/steps/hourly` supplies only the latest 24 hours and ignores historical window parameters, so it cannot provide a weekly accepted-step total. Seat rankings separately count accepted contributions within the covered week, including those in blocked jobs. The 6,504 contributions with seat numbers give Seat #1814 (72), Seat #398 (51) and Seat #1211 (44). Eighteen accepted panel records have no seat number and are explicitly left unattributed. Online is `connectedDaemons` from `/health`, a reporting-time snapshot rather than a weekly total.

[`evidence/003.json`](evidence/003.json) contains the notes embedded in “How we counted,” the ranking explanation and the watch story’s source. [`artifacts/003-counts.json`](artifacts/003-counts.json) preserves the relevant dated counting rows and pagination trail. [`artifacts/003-story-evidence.json`](artifacts/003-story-evidence.json) records publication dates, selected findings and decoded answers. The existing `npm run check` recalculates the saved trail offline. Earlier editions’ raw counting trails are absent and are reported as not re-checked; their files are preserved.

These checks support editorial review. They do not independently certify the API’s historical completeness, cryptographic signatures, third-party application security or real-world claims behind an answer. Audit stories describe findings in reviewed versions, without implying a live loss or a confirmed repair. Duplicate, promotional, offensive and copycat projects were excluded from story selection. Aggregate counts cover the API’s records, not only the selected stories.

## Actual validation

The final production build, TypeScript check and content/evidence checks passed. All **58 Chromium interaction checks** passed, with no application console errors, failed application resources or automated accessibility violations at the five tested widths. The pinned design probe passed 9 of 16 checks; its inherited newspaper-style exceptions and false column-overlap flag are explained in the review. A WebKit launch failed because required system libraries were unavailable, so Safari is unverified.

See [`docs/validation-003.md`](docs/validation-003.md) for the commands actually run, final results, all six Better Interface review domains, the pinned design probe’s findings, screenshots and limitations. Historical validation for issue 002 remains in [`docs/validation-002.md`](docs/validation-002.md). This is worker-side validation, not independent certification.

The new ignore file allows only nine named evidence files under `artifacts/`, with an explicit 3.75 MiB path budget: 2.5 MiB for JSON and 1.25 MiB for screenshots. The remaining 4.25 MiB is reserved for the complete source, lockfile, documentation and runtime export. This overrides an existing local exclusion for that directory without changing Git configuration. Dependency and cache directories remain excluded at every nesting level.

## Add another edition

1. Read the public API with your own `User-Agent` and gather the most recent complete Monday–Sunday UTC week.
2. Add the next numbered `issues/NNN.json` using the existing schema. Do not edit earlier editions. `date` is the publication date; `week` describes the reporting period.
3. Add its `evidence/NNN.json` notes and compact counting/story trails. Weekly leaders count all accepted nodes dated in the week, with their recorded seats, regardless of the parent job’s final state. Use `leadersScope: "all time"` only when a weekly count cannot be made; missing scope means all-time for older editions.
4. Build, typecheck, validate the content and interactions, and include the complete rebuilt `dist/`. All issue tabs, Latest, index and feed are generated from the numbered files.

## Source map

| Path | Purpose |
| --- | --- |
| `issues/` | Numbered editions and generated newest-first index |
| `evidence/` | Per-edition notes embedded in the paper |
| `src/` | Existing newspaper, interactions and responsive styles |
| `scripts/` | Existing build-time content, evidence and browser checks |
| `public/` | Local favicon, share image and runtime license notices |
| `dist/` | Complete static export, including RSS and local assets |
| `DESIGN.md` | Implemented tokens, typography, components and responsive rules |
| `docs/` | Edition reviews and design-guidance attribution |
| `artifacts/` | Compact reporting trail and actual validation results |

The supplied Better Interface guide informed the review. Its original attribution and included licenses are retained in [`docs/design-guidance-licenses.txt`](docs/design-guidance-licenses.txt). Runtime library notices remain in the export.
