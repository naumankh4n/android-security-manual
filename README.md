# Android Security Field Manual

An interactive, single-file study tool for Android app pentesting interviews — manifest analysis, storage, network, component vulnerabilities, auth, Frida/dynamic analysis, root detection, and deep links, plus 13 scenario-based practice drills.

No build step, no dependencies to install, no backend. It's one HTML file.

## Features

- **Study mode** — flip-card drills, one question at a time, per topic area
- **Browse mode** — every question and answer in a scannable, expandable list
- **Scenario drills** — 13 interview-style scenarios broken into checkable, step-by-step model answers
- **"10 to lock in first"** — a priority checklist for last-minute review, linking straight to each topic
- **Search** — filters every question and answer at once, across all topics and scenarios
- **Progress tracking** — mark questions as reviewed or flag them for a second pass; a running completion percentage is shown in the header
- **Keyboard shortcuts** — `←` / `→` to move between cards, `space` to flip, `K` to mark the current card reviewed
- Fully responsive, keyboard-accessible, and respects `prefers-reduced-motion`

## Topics covered

| Area | Questions |
|---|---|
| Android fundamentals | 20 |
| APK static analysis | 17 |
| Data and storage | 13 |
| Network security | 13 |
| Component vulnerabilities | 14 |
| Authentication and authorization | 12 |
| Reverse engineering and dynamic analysis | 11 |
| Root and device security | 10 |
| Deep links | 7 |
| Scenario drills | 13 |
| **Total** | **130** |

## Getting started

Clone the repo and open the file in any browser:

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
open android_field_manual.html   # macOS
# or just double-click it in Finder/Explorer, or drag it into a browser tab
```

No server, no npm install, no build — it's plain HTML, CSS, and vanilla JavaScript in a single file.

## Progress saving

When opened inside a Claude.ai artifact, progress (reviewed/flagged questions, checked-off scenario steps) is saved automatically through Claude's artifact storage API and persists across sessions.

When opened as a plain local file or hosted elsewhere, the site still works fully, but progress won't persist between page loads unless you add your own storage (see [Customizing](#customizing) below).

## Customizing

All content lives in two arrays near the top of the `<script>` block:

- `DATA` — an object keyed by topic, each with a `name`, an icon `glyph`, and an `items` array of `{ id, q, a }` objects
- `SCENARIOS` — an array of `{ id, orig, prompt, steps }` objects for the scenario drills
- `PRIORITY` — the "10 to lock in first" checklist, each pointing at a topic key via `cat`

To add a question, add a new `{ id, q, a }` object to the relevant topic's `items` array with a unique `id`. To add a topic, add a new key to `DATA` with a `name`, `glyph`, and `items` array — it'll pick up navigation and progress tracking automatically.

To swap the in-artifact storage for `localStorage` (for a plain self-hosted deploy), replace the calls in `loadProgress()` and `saveProgress()` with `localStorage.getItem` / `localStorage.setItem`.

## Tech

Vanilla HTML, CSS, and JavaScript. IBM Plex Sans and IBM Plex Mono loaded from Google Fonts. No frameworks, no build tooling.

## License

Add a license of your choice (MIT is a reasonable default for a study tool like this).
