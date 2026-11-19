# Changelog

All notable changes to Long Island Fire Tracker are documented here.

This project follows [Semantic Versioning](https://semver.org/): `vMAJOR.MINOR.PATCH`

| Part | When to bump | Example |
|------|-------------|---------|
| **MAJOR** | Breaking change to `fires.json` format, or complete UI overhaul | `v2.0.0` → `v3.0.0` |
| **MINOR** | New tab, new chart, or new feature | `v2.0.7` → `v2.1.0` |
| **PATCH** | Bug fix, label tweak, or cosmetic change | `v2.0.7` → `v2.0.8` |

---

## [v2.4.0] — 2026-11-19

- In Progress: a partial month no longer skews the numbers. "Pace vs" and "vs Historical Avg" now compare at the same point in the month (for example Nov 1–19 against 19/30 of last November), and Projected Full Year counts the partial month as fires so far plus the historical average for the days left. The month projection card now follows the data's last update date, not today's date. On the chart, the partial month's projection shows as a faded bar behind the solid yellow bar
- Overview: new strip at the top showing the current year's fires so far compared with last year at the same point. Clicking it opens In Progress
- Monthly Grid: both grids now include the year in progress as a highlighted row below the completed years, with an unfinished month in yellow. It doesn't change the color scale or the Avg row. Removed an unused current-year check from the battalion grid

## [v2.3.8] — 2026-11-19

- In Progress tab: a month that isn't over yet (when `last_updated` falls before the month's last day) now shows in yellow, not red, so it doesn't look final. This covers its bar and point on the charts, its column in the department table, and its own legend entry. "Through", "thru" and "Pace vs" labels now give the day (for example "Nov 19"), and Year Progress counts the partial month by days

## [v2.3.7] — 2026-11-19

- Fixed stat cards and charts looking dim: each tab faded in from transparent, and on a busy page load that 0.2-second fade could stall part-way (measured at 37% opacity three seconds after load), leaving the whole tab dim. Tabs now slide in without any fade, and animations are off for people who turn on Reduce Motion
- Chart bars are brighter (the blue annual and monthly bars were 20% opacity), and axis and legend text is lighter
- Contrast: zero-fire table cells, the selected battalion row, and white text on orange buttons and pills now meet WCAG AA
- Keyboard: year pills can be reached with Tab and pressed with Enter or Space, and focused controls show a yellow outline
- Loading: `fires.json` now times out after 15 seconds, and the error screen has a **Try again** button; the error text is escaped
- Department and battalion names from `fires.json` can no longer be read as HTML
- Add to Home Screen: added a flame app icon, web app manifest and theme colour; the stylesheet now sits inside `<head>`
- `.gitignore`: ignore `.claude/settings.local.json` and `.claude/worktrees/`

## [v2.3.6] — 2026-10-22

- iPhone: the header's background now extends under the Dynamic Island / status bar and its title and county buttons start just below it, so iOS no longer blurs the top of the header. In landscape the page keeps clear of the notch, and the pinned footer clears the home indicator

## [v2.3.5] — 2026-10-11

- GitHub account renamed from RLeone37 to RJLcode: updated `LICENSE`, the source header and footer in `index.html`, and the README's live-site links and License section. The live site is now at https://rjlcode.github.io/LongIslandFireTracker/

## [v2.3.4] — 2026-09-30

- Footer is now pinned to the bottom of the window, so the version, data date, and copyright notice are always visible instead of only after scrolling to the end of the page

## [v2.3.3] — 2026-09-30

- Standardized copyright and license notices to match RLeone37's other projects: updated `LICENSE` wording (explicitly not open source), expanded the source header in `index.html`, footer now reads "© 2026 RLeone37. All Rights Reserved." with a License link to GitHub, and refreshed the README License section

## [v2.3.2] — 2026-09-30

- Footer now links to `LICENSE` with a visible "© 2026 All Rights Reserved" notice, so the site's proprietary terms are apparent to every visitor, not just people who find the LICENSE file in the repo

## [v2.3.1] — 2026-09-30

- Added a copyright/license notice comment to the top of `index.html` so the "all rights reserved" terms are visible in the source itself, not just in `LICENSE`

## [v2.3.0] — 2026-09-30

- Trends tab's Annual Totals line chart now includes the current in-progress year (e.g. 2026), shown as a dashed segment ending in a yellow point labeled "(YTD)" so it's visually distinct from completed years; applies uniformly to both Nassau and Suffolk

## [v2.2.0] — 2026-09-29

- On load, `fires.json` is now validated: department name mismatches between `departments` and `years`, arrays without exactly 12 entries, and non-numeric monthly values are caught and surfaced as a dismissible warning banner (plus `console.warn`) instead of silently reading as 0

## [v2.1.3] — 2026-05-04

- Records tab tiles now highlight on hover, matching behavior of other tabs

## [v2.1.2] — 2026-05-04

- Removed Update Data tab from both Nassau and Suffolk — nav button, tab content, password check, and all associated JS removed

## [v2.1.1] — 2026-05-04

- In Progress tab: renamed "Month Trend" stat card label to "Month Projection" for consistency with tab's projection terminology

## [v2.1.0] — 2026-05-04

- In Progress tab: added Pace vs Last Year stat card — shows "On Track / Ahead / Behind" compared to the prior year's fire count through the same month
- In Progress tab: added Month Trend stat card — projects current month's final count based on days elapsed (if partial data exists) or historical average
- README: removed dev branch preview link and dev/hotfix branch strategy; main is the only branch
- CLAUDE.md: removed dev branch workflow references

## [v2.0.8] — 2026-05-04

- Battalion/Division Monthly Grid now highlights the current month column header, matching the county-wide Monthly Fire Grid

## [v2.0.7] — 2026-05-03

- Most Active Battalion/Division stat card now auto-scales font size to prevent text from being cut off
- Removed logo from header
- Removed colored dot indicators from all chart and graph titles
- Chart titles upgraded: brighter text color, added bottom border separator
- Chart cards now have a 2px accent-colored top border
- Section headers restyled: CSS bar element replaces text character, fire-orange color, heavier weight
- Battalion/division labels reformatted to ordinal-first across all charts, legends, and tables (e.g. "1st Battalion", "3rd Division") for Nassau and Suffolk
- Battalion/Division Share and Stacked charts now use full spelled-out labels consistent with the above format
- Departments table column header now reads "Battalion" or "Division" depending on county (was abbreviated "Bat.")
- Department names no longer display "F.D." suffix in any table across Nassau and Suffolk
- Most Active Dept stat card (Overview) now correctly strips "F.D." from the displayed department name
- Removed proportional bar indicators from department name cells in the Departments table

## [v2.0.6] — 2026-05-03

- Average Monthly Pattern chart (Overview) peak bar no longer highlights in orange — all bars now uniform blue
- Annual Totals bar chart (Overview) peak bar no longer highlights in red — all bars now uniform blue
- In Progress tab subtitle updated from "Solid = actual" to "Red = actual" for clarity

## [v2.0.5] — 2026-05-03

- Added logo to header beneath title

## [v2.0.4] — 2026-05-03

- Replaced last data update date in header with version number
- Added version comment at top of `index.html`

## [v2.0.3] and earlier

- Battalions tab renamed to Battalions/Divisions
- Most Active Division stat card abbreviates "Division" to "Div" (consistent with "Bn" for Battalion)
- Average Monthly Pattern chart no longer highlights the peak month — all bars use uniform blue
- Removed rolling-average lines and table columns
- Monthly Fire Grid highlights only the current month name in the header
- Battalion Monthly Grid includes an Avg row matching the Monthly Fire Grid style
- Header date label changed to `Last data update:`
- Dashboard loads `fires.json` with `cache: no-store` and shows a clear error if the file is missing or invalid
