# Behavior Tracker (Verhaltens-Tracker)

A free, single-file web app for recording the behavior of **cattle, pigs and sheep** in the barn, on pasture or from video. Tap a button when a behavior starts, tap it again when it ends. The app stores start and end times, and turns them into time budgets, daily patterns, bouts, transitions, synchrony and heatmaps.

It is built for **farmers** (quick checks, welfare indicators) and **scientists** (ethogram editing, scan sampling, CSV/JSON export, BORIS-style output). It runs in any modern browser on a phone, tablet or laptop, in English and German.

> **Try it online:** <https://jensharbers.github.io/AnimalObservation/Tierverhalten/>
> No account, no installation. Your data never leaves your device.

![Recording screen](docs/screenshots/03_record.png)

*(All screenshots in this repository use generated demo data, not real animals.)*

---

## Contents

1. [Highlights](#highlights)
2. [Quick start](#quick-start)
3. [Run it locally and offline](#run-it-locally-and-offline)
4. [Interface tour (left to right, top to bottom)](#interface-tour-left-to-right-top-to-bottom)
5. [Built-in ethogram](#built-in-ethogram)
6. [Data, export and backup](#data-export-and-backup)
7. [Privacy](#privacy)
8. [Scientific notes and limitations](#scientific-notes-and-limitations)
9. [Browser support and permissions](#browser-support-and-permissions)
10. [Illustrated walkthrough (vignette)](#illustrated-walkthrough-vignette)
11. [Third-party components](#third-party-components)
12. [License](#license)

---

## Highlights

- **One tap per behavior**, several behaviors at once (e.g. *Standing* + *Ruminating*), timers on every active button.
- **32 built-in behaviors** in 8 groups, filtered by species. Add your own, hide what you do not need.
- **Single-animal recording** and **herd scan sampling** (what is each animal doing right now?).
- **Reminder timer** (every x seconds or minutes) with sound and vibration that stores a snapshot of all animals.
- **Analysis in the app:** duration tables, Gantt chart, welfare-indicator presets, five chart types, day/time heatmap.
- **Export:** JSON, three CSV flavours (events, START/STOP, scans), BORIS-like CSV and 1-second grid CSV for agreement statistics, PDF/print report, calendar reminders (ICS), LaTeX Beamer folder (ZIP) for the heatmap.
- **Merge colleagues' data** from a JSON file, so several observers can work on the same trial.
- **Field-ready:** outdoor mode (black/yellow, large buttons), night mode (red light), screen lock, screen stays on while recording, vibration feedback, screen-reader support.
- **Works offline** once the files are on your device, and keeps everything in the browser.

## Software Features and Functional Scope

AnimalObservation combines behavioural data collection, data management and exploratory analysis in a single browser-based application.

### Behavioural data collection

The application supports individual animal observations and group-based herd scans. Behaviours can be recorded using start/stop interactions, allowing the simultaneous recording of multiple behaviours per animal.

Each observation can be associated with animal identification, species, observer, study, group, location and additional session metadata.

### Configurable ethograms

The built-in ethogram contains 32 predefined behaviours for cattle, pigs and sheep, organized into eight behavioural categories.

Users can add their own behaviours, edit definitions and examples, and configure which behaviours are displayed for each observation scenario.

### Observation methods

The application supports:

- Continuous behavioural recording using start/stop events.
- Individual animal observations.
- Group observations and scan sampling.
- Interval-based observation reminders.
- Recording of simultaneous behaviours.
- GPS-supported location tagging, where available.

### Data analysis and visualization

AnimalObservation provides integrated tools for exploratory behavioural analysis, including:

- Behavioural time budgets.
- Daily activity patterns.
- Behavioural bout analysis.
- Behavioural transition analysis.
- Synchrony analysis.
- Herd scan summaries.
- Behavioural heatmaps.
- Configurable welfare-related indicators.

### Data management and interoperability

Observation data can be exported in several formats, including JSON and CSV.

Additional export options include BORIS-style event data, one-second observation grids for agreement statistics, PDF reports and visualization exports.

The application also supports merging observation datasets from different observers.

### Field-oriented interface

The interface includes features designed for practical observation environments:

- Outdoor mode with high-contrast colours and large buttons.
- Red-light night mode.
- Screen lock to prevent accidental input.
- Screen wake lock during recording, where supported.
- Vibration and audio feedback.
- Keyboard and screen-reader accessibility support.

These features are intended to facilitate data collection in barns, on pasture and during video-based observations.

## Quick start

1. Open the [online version](https://jensharbers.github.io/AnimalObservation/Tierverhalten/).
2. **Animals** tab: enter a name and/or a number, choose the species, tap **Add animal**.
3. **Record** tab: choose an animal at the top, then tap behaviors as you see them. Tap again to end a behavior.
4. **Data** tab: tap **Export JSON** (or a CSV button) to save your data.

Want to look around first? Open **Data → ⚙ → Load demo data (6 cows, 2 days)**. Remove it again with **Remove demo data**.

## Demonstration Datasets

AnimalObservation includes four predefined demonstration datasets that allow users to explore the application's functionality without collecting their own observational data.

The datasets are synthetically generated for demonstration and testing purposes. They do not represent empirical observations and must not be interpreted as evidence of actual animal behaviour patterns.

They are intended to illustrate different aspects of behavioural data collection and analysis.

### Purpose of the demonstration datasets

The datasets support:

- Familiarization with the recording interface.
- Demonstration of behavioural time budgets and activity patterns.
- Exploration of behavioural sequences and transitions.
- Testing of data export and visualization functions.
- Reproducible demonstrations in teaching and research contexts.

### Loading demonstration data

Demonstration data can be loaded directly from the application:

1. Open the Data tab.
2. Select the additional options menu (⚙).
3. Choose Load demo data.
4. Explore the available recording and analysis functions.

The demonstration data can be removed again using Remove demo data.

### Importing user datasets

In addition to the predefined demonstration datasets, users can import their own observation datasets.

This allows AnimalObservation to be adapted to different animal species, research questions and observation scenarios.

The distinction between synthetic demonstration data and empirical research data is maintained throughout the documentation.

## Run it locally and offline

## Installation and Deployment

AnimalObservation is a self-contained static web application. It does not require a database, backend server, user account or installation of additional software packages.

### Local installation

1. Download or clone the repository from GitHub.
2. Extract the downloaded files if necessary.
3. Open the project folder.
4. Open `index.html` in a modern web browser.

The application can be used directly from the local file system. Recording, data management, analysis and data export are available without running a web server.

### Recommended local deployment

For features that require a secure browser context, such as camera access, GPS tagging and service worker registration, a local web server is recommended.

From the project directory, run:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

### Offline deployment

For fully offline operation, all required application files and third-party JavaScript libraries must be available locally.

The following libraries should be kept in the project directory:

- `lib/jszip.min.js`
- `lib/jsQR.min.js`
- `plotly-cartesian.min.js`

This prevents the application from attempting to retrieve missing libraries from external content delivery networks.

The application can subsequently be used without an active internet connection.

### Supported platforms

AnimalObservation runs in current versions of Chrome, Edge, Firefox and Safari on desktop computers, tablets and smartphones.

No central infrastructure or cloud service is required. Data is stored locally in the browser of the device being used.


The app is a static page. There is nothing to build and no server component.

**Option A: just open the file.** Download this folder and open `index.html` in your browser. Recording, analysis and export work.

**Option B: serve it locally (recommended).** Some browser features (camera for QR scanning, GPS, service worker for offline use) only work in a *secure context*, i.e. `https://` or `http://localhost`. From the project folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

**Option C: put it on your phone like an app.** Host the folder on any static web host (for example GitHub Pages), open the address in Chrome (Android) or Safari (iOS), and use *Add to Home screen* / *Install app*. If a `sw.js` file is deployed next to `index.html`, the app registers it as a service worker for offline use.

**Keep it truly local (no internet at all).** The app uses three small libraries. It looks for them next to the HTML file first and only falls back to a public CDN if they are missing. To avoid any network request, keep these files in place:

| File | Needed for |
|---|---|
| `lib/jszip.min.js` | ZIP export (Beamer folder) |
| `lib/jsQR.min.js` | QR scan on browsers without the built-in `BarcodeDetector` |
| `plotly-cartesian.min.js` | Heatmap |

Recording, tables, charts and CSV/JSON export need none of them.

## Interface tour (left to right, top to bottom)

### Header (always visible)

| Element | What it does |
|---|---|
| **Title** | "Behavior Tracker" (or "Verhaltens-Tracker" in German). |
| **🔒 Lock** | Locks the screen so nothing is tapped by accident (pocket, gloves, rain). Hold the *Hold to unlock* button for about 2 seconds to unlock. |
| **Theme button** (◐ / ☀︎ / ☾) | Switches between day mode, **outdoor mode** (black/yellow, larger buttons and spacing, for sunlight and gloves) and **night mode** (red light, does not dazzle you or the animals). Hold it for 3 seconds to switch, which prevents accidental changes. |
| **EN / DE** | Switches the interface language. The button shows the language you will switch *to*. |
| **?** | Short "How it works" help. Every card has its own **?** with details. |

A **Skip to content** link is available for keyboard and screen-reader users.

### Navigation bar (bottom, left to right)

**Animals · Record · Analysis · Data · Info**

---

### 1. Animals

![Animals tab](docs/screenshots/01_animals.png)

From top to bottom:

1. **Add animal card**
   - *Name* and *Number* fields. At least one is required (for example "Berta", "DE 0123", "17 · Hannah").
   - *Species* selector: Cattle, Pig or Sheep. The species decides which behaviors are offered.
   - **📷 Scan QR code**: adds an animal from a QR code that contains the ear-tag number or name (needs camera permission).
   - **Add animal**.
2. **Your animals (n)** card: a filter box, then the list of animals with a **Delete** button each. Deleting an animal also deletes its data (you are asked to confirm).
3. **Session card** (study metadata): *Study / project*, *Observer*, *Group / pen*, *Location*, *Temp. °C*, *Housing system* and a free-text *Day note*. These values are saved with every **newly started** event and appear in the JSON and CSV exports. Tip: enter your name as observer, so your records stay identifiable after merging with a colleague's data.
4. **Ethogram editor**: add your own behavior (name, definition/example, main category, species), and open the **Ethogram (32)** list to show or hide behaviors (● shown, ○ hidden) or delete your own behaviors with × (only possible while no data uses them; hide instead).

![Session and ethogram editor](docs/screenshots/02_session_ethogram.png)

### 2. Record

![Recording with active behaviors](docs/screenshots/04_record_active.png)

From top to bottom:

1. **Notices:** a running validation timer (if you started one) and a reminder to export if your last export is older than a day.
2. **Mode bar (left to right):** **Single animal** · **Herd** · **📷 QR** (select an animal by scanning its ear-tag code) · **?**
3. **Animal chips:** tap to choose which animal you are recording. Swipe sideways if there are many.
4. **Reminder card:**
   - *every* [number] [seconds | minutes], **Start** / **Stop**. When the interval elapses you get a sound and vibration; confirm, and the current state of all animals is saved as a snapshot.
   - **Record now** saves a snapshot immediately.
   - **📍** switches GPS tagging on or off (location is stored with records when allowed).
   - **Size** XL / L / M / S: one, two, three or four buttons per row. Use S to see everything at once, XL for big targets.
   - **↶ Undo** reverts the last start or stop.
   - **?** explains the screen.
5. **Out of sight** (dashed button): press while the animal cannot be observed. This time is excluded from the behavior denominators.
6. **Behavior buttons**, grouped by category (Resting, Locomotion, Feeding, Maintenance, Social, Exploration, Maternal, Other). Within a group, the behaviors you use most appear first.
   - Tap = start (button turns green and shows the running time). Tap again = end.
   - Several buttons can be active at the same time.
   - The **?** on a button shows its definition and example.
   - Feedback is given by colour, text, vibration (short = start, double = end) and a screen-reader announcement.
   - The screen stays on while this tab is open.

![Button sizes](docs/screenshots/06_record_size_S.png)

**Herd scan (scan sampling).** Switch to **Herd** and tap **Herd scan (n)**. For each animal in turn, choose the behavior(s) at the moment of the scan and tap **Save & next**, or **Skip** if the animal is not visible. The chips at the top show progress (✓ recorded, – skipped); tap one to correct it. **End scan** stops the pass. All animals of one pass share the same scan ID and start time. The reminder timer can prompt you for scans at fixed intervals.

![Herd scan](docs/screenshots/07_herd_scan_start.png)

### 3. Analysis

Three sub-tabs, left to right: **Tables · Charts · Heatmap**.

#### Tables

![Tables](docs/screenshots/09_analysis_tables.png)

1. **Animal chips** to choose the animal.
2. **Duration per behavior:** choose the resolution (*Day* or *Hour*) and a date. The table shows duration per behavior and day (or hour), the total (Σ duration) and the event count. Darker cells mean longer durations. Overlapping behaviors are counted separately, so totals can exceed the observation time.
3. **Gantt chart** of the selected date: one bar per behavior over the time of day. Long-press a bar to see its start and end.
4. **Herd scan summary** (appears once you have scans): share of animals per behavior for each scan.
5. **Welfare indicators:** preset buttons *Cattle welfare*, *Pig welfare*, *Sheep welfare* and *Show all*. A preset hides behaviors that are not needed for the topic and creates matching indicators. The table shows, per animal and selected day, a duration (min) or a count. Enter a threshold (≥) and values at or above it turn red. **No thresholds are preset**; set them from literature or farm standards. Use *Add indicator* for your own (behavior + duration or count). The presets are pragmatic selections, not validated welfare protocols.

#### Charts

![Time budget chart](docs/screenshots/10_chart_timebudget.png)

1. **Chart type:** *Time budget* · *Daily pattern* · *Bouts* · *Transitions* · *Synchrony*.
2. **Scope:** *Single animal* or *Herd mean*. In herd mode, chips with ✓ / ✕ include or exclude single animals from the mean (tap to toggle). Species are never mixed; if you have several species, species chips appear.
3. **Date** (*All days* or one day) and, for some charts, a **behavior** selector.
4. **The chart,** with the number of animals and a one-line explanation:
   - *Time budget*: share of observed time per behavior (bar = mean, line = ±SD, dots = individual animals).
   - *Daily pattern*: minutes per hour over the day for one behavior.
   - *Bouts*: mean bout duration (x) against bouts per day (y), one dot per animal.
   - *Transitions*: which behavior follows which (row to column, share within the row).
   - *Synchrony*: share of observed animals showing the behavior, in 5-minute steps.

   More examples: [daily pattern](docs/screenshots/11_chart_daily.png), [bouts](docs/screenshots/12_chart_bouts.png), [transitions](docs/screenshots/13_chart_transitions.png), [synchrony](docs/screenshots/14_chart_synchrony.png).

The **?** next to *Charts* explains when to exclude an animal from the herd mean (sick, in estrus, different pen or age, too little data, test data, or when comparing one animal against the rest of the herd).

#### Heatmap

![Heatmap](docs/screenshots/15_heatmap.png)

1. **Animal chips:** which animals contribute.
2. **Aggregation period (x-axis):** *Each day*, *Weekday (averaged)* or *Calendar week*.
3. **Resolution (y-axis):** 5, 15, 30 or 60 minutes of the day.
4. **Hide edge days:** removes the first and last observation day, which are often only partly covered.
5. **Metric:** *Dominant behavior* (colour by the longest-lasting behavior), *Share of one behavior* (a behavior selector appears), *Behavioral diversity (entropy)*, *Number of behaviors*, or *Recorded time (coverage)*.
6. **The plot.** Click or tap a cell to see its values, the share per behavior and a list of individual events; tap an event to open the event editor. The chart is editable (double-click labels).
7. **Export buttons:** *Export PNG*, *Matrix as CSV*, *Raw data as JSON*, *Beamer folder (.zip)* (LaTeX slides; compile with `latexmk -pdf main.tex`, needs `beamer`, `pgfplots`, `pgfplotstable`, `booktabs`, or upload the ZIP to Overleaf).

The heatmap needs Plotly (`plotly-cartesian.min.js`). If neither the local file nor the internet is available, the app tells you so and offers *Try again*.

### 4. Data

![Data tab](docs/screenshots/16_data.png)

From top to bottom:

1. **Backup notice:** "No automatic backup – export regularly", plus the time of your last export.
2. **Animals / events / snapshots** card with counts, a **⚙ More options** button and a **?**:
   - **Export JSON** (full data set) and **Copy** (to clipboard).
   - **CSV (events)**, **CSV (START/STOP)**, **CSV (scans)**.
   - **Merge colleagues' data (JSON)** and **From clipboard**: shows a preview of what is new before you confirm. Animals are matched by ID or by number/name plus species; events and scans already present are not imported twice, so importing the same file again is safe. Behaviors still running in the file are closed at the export time.
3. **Validation card** (comparison with a reference tool such as BORIS): enter a video/observation ID and video length, press **● Start observation** when the video starts and **■ End observation** when it ends. The app measures coding time, counts inputs and computes coding time ÷ video length. Per observation you can export **BORIS CSV** (START/STOP events in seconds from observation start) or **Grid CSV** (state per second and animal, suitable for Cohen's kappa). **Study protocol template (.md)** downloads a ready-made outline for a validation study.
4. **⚙ More options** (opens as an extra card):
   - **PDF/print report** and **Reminders (ICS)** (calendar entries for your interval).
   - **Export / Import ethogram** and **Codebook (JSON)**.
   - **Load demo data** / **Remove demo data**.
   - **Optional secondary backup:** on Chrome/Edge you can pick a file (for example on an SD card or USB stick) that the app mirrors your data to. This is an extra copy, not a live mirror, and it depends on the browser and device. Without it, a normal JSON export is enough.
5. **Recent events** (last 30, newest first). Tap an event to correct its behavior, start and end, or to delete it. A change history is kept per event.
6. **Delete all data** (red). Asks for confirmation.

![More options](docs/screenshots/17_more_options.png)

### 5. Info

Short description of the app, a link to the author's website and the legal notice (Impressum).

![Info](docs/screenshots/18_info.png)

## Built-in ethogram

32 behaviors, shown according to the species of the selected animal (C = cattle, P = pig, S = sheep).

| Group | Behaviors |
|---|---|
| Resting | Lying (all) |
| Locomotion | Walking, Postural transition (all) |
| Feeding & drinking | Feeding, Drinking (all) · Grazing, Ruminating (C, S) · Rooting (P) · Browsing (S) |
| Maintenance | Grooming, Elimination (all) · Scratching (C) |
| Social | Social interaction, Aggression / fighting, Play (all) · Licking (C) · Mounting (C, P) · Tail biting (P) · Flocking, Isolation, Head butting (S) |
| Exploration | Exploration (all) · Nosing, Manipulating objects (P) |
| Maternal | Calf nursing (C) · Nesting, Suckling (P) · Lamb nursing (S) |
| Other | Other / unclassified (all) · Heat stress behavior (C) · Vigilance (S) |

*Standing* belongs to *Resting* and is available for all species. Every behavior has a short definition and example behind its **?** button. You can export the ethogram (including definitions) as JSON and import it on another device; only new behaviors are imported.

## Data, export and backup

- Times are stored and exported in **UTC (ISO 8601)**. Heatmap bins follow your local wall clock.
- **JSON export** contains animals, events (start, end, duration in seconds), snapshots/scans, session metadata, observations and the behavior table:

```json
{
  "animals": [{ "id": "a1", "name": "Berta", "number": "17" }],
  "events": [{
    "animalId": "a1",
    "behavior": "ruminating",
    "start": "2026-10-27T08:00:00Z",
    "durationSec": 420
  }]
}
```

- **CSV (events):** one row per event, with behavior in English and German, main category, start/end (UTC), duration, study, observer, group, location and more. **CSV (START/STOP):** one row per start or stop, BORIS-like, time in seconds from the first event. **CSV (scans):** all herd-scan and snapshot data. All CSV files are comma-separated, UTF-8.
- The app does **not** back up automatically. Export regularly, especially before clearing browser data or switching devices.
- Multi-device work: export on one device, then use **Merge colleagues' data** on the other.

## Privacy

All data stays in your browser (`localStorage` plus IndexedDB, soft limit about 15 MB). Nothing is sent to a server, and there is no tracking or account. Clearing your browser data deletes your records, so export first. GPS, camera and the optional backup file are only used when you switch them on and allow them. If a local library file is missing, the page may load it once from a public CDN (jsDelivr or cdnjs); keep the files from `lib/` next to the page to avoid this.

## Scientific Background and Research Relevance

### Motivation

Systematic behavioural observation is an established method in animal science, ethology and livestock research. However, behavioural data collection in practical research environments can involve heterogeneous recording procedures, manual documentation and subsequent transfer of observations into digital analysis tools.

AnimalObservation was developed to provide an integrated digital environment for recording, managing and exploring animal behaviour data.

The software aims to simplify structured behavioural observations while supporting consistent data handling and subsequent analysis.

### Research applications

AnimalObservation is designed for use in different research and educational contexts, including:

- Behavioural studies in cattle, pigs and sheep.
- Animal welfare research.
- Livestock behaviour monitoring.
- Individual and group-based behavioural observations.
- Teaching and practical training in animal science and ethology.
- Video-based behavioural coding.

### Standardized data collection

The application combines configurable ethograms with structured recording procedures.

Behavioural events are stored with timestamps and associated metadata. This provides a consistent data structure for subsequent analysis, comparison and export.

The availability of configurable ethograms allows researchers to adapt behavioural categories and definitions to their specific research questions.

### Field applicability

A particular design objective is the use of the application under practical observation conditions.

The browser-based architecture allows deployment on smartphones, tablets and laptops without requiring a central server or permanent internet connection.

Local data storage supports observations in environments where network connectivity is limited or unavailable.

Features such as outdoor mode, night mode, screen locking and vibration feedback are intended to facilitate operation under different environmental conditions.

### Reproducibility and data interoperability

AnimalObservation provides structured data exports in JSON and several CSV formats, including event-based and scan-based representations.

The availability of BORIS-style event exports and one-second observation grids supports data exchange and comparison with other behavioural coding workflows.

Synthetic demonstration datasets allow users to explore the application and reproduce software demonstrations without requiring access to empirical research data.

### Scope and scientific limitations

AnimalObservation is a research support tool for behavioural data collection and exploratory analysis.

The software does not replace the development and validation of species-specific ethograms, observation protocols or experimental designs.

Researchers remain responsible for defining appropriate behavioural categories, establishing observation procedures and assessing the reliability and validity of their collected data.

## Scientific notes and limitations

- The ethogram is a practical starting point, **not a validated protocol**. Adapt definitions to your question and document them for publication.
- The analysis views, especially the heatmap, are **exploratory**. Heatmap denominators are cell duration × number of contributing animal-days; unrecorded time cannot be told apart from "behavior not shown". Check *Coverage* before interpreting other metrics. On daylight-saving transition days the repeated or missing hour remains ambiguous.
- Overlapping behaviors are counted separately, so shares can add up to more than 100 %.
- The welfare presets pick behaviors from the ethogram; thresholds are intentionally left to you.
- Reminder timers and the wake lock need the page to stay open with the screen on.
- Storage is limited to roughly 15 MB per browser. When full, the app asks you to export and delete old entries.

## Browser support and permissions

Current Chrome, Edge, Firefox and Safari on Android, iOS and desktop. Some features depend on the browser:

| Feature | Needs |
|---|---|
| QR scan | Camera permission and a secure context; uses `BarcodeDetector` where available, otherwise jsQR |
| GPS tagging | Location permission |
| Screen stays on | Screen Wake Lock API |
| Vibration | Vibration API (not on iOS Safari) |
| Secondary backup file | File System Access API (Chrome/Edge; often missing in Safari/Firefox) |
| Offline use via service worker | Secure context and a deployed `sw.js` |

## Illustrated walkthrough (vignette)

A step-by-step tour with screenshots (demo data, outdoor and night mode, screen lock) is in [`docs/VIGNETTE.md`](docs/VIGNETTE.md).

## Third-party components

JSZip (MIT or GPL-3.0, used under MIT), jsQR (Apache-2.0) and Plotly.js (MIT). Details and license texts: [`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md) and `lib/licenses/`.

## License

Released under the [MIT License](LICENSE). You may use, copy, modify and redistribute the app, including in research and commercial settings, as long as the copyright and license notice stay with it.

## Author and feedback

Jens Harbers, [harbers-agrarinformatik.de](https://harbers-agrarinformatik.de). Questions, ideas and bug reports are welcome as GitHub issues.
