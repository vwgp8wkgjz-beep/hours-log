# Hours log

One-page timesheet you install as an app. Type hours per day, export to Excel.

Live at: https://vwgp8wkgjz-beep.github.io/hours-log/

## Install it on a computer

1. Open the link above in Chrome or Edge.
2. Chrome: click the install icon at the right end of the address bar. Edge: menu (three dots), then Apps, then "Install this site as an app."
3. It gets its own icon and window, and opens without internet after the first visit.

No admin rights needed. A locked-down work computer can still block it through browser policy; that is an IT setting.

## What it does

- Week view, Monday to Sunday. Type hours as `7.5` or `7:30`, plus an optional note per day.
- "All weeks" list with weekly totals and a grand total. Click a week to open it.
- **Export to Excel** downloads a `.xlsx` with two sheets: "All weeks" (day by day, with week totals) and "Weekly totals".
- **Save shareable copy** downloads a single `.html` file: this same page, read-only, with the hours inside it. The recipient opens it in any browser and can export Excel from it too.

## How it works

- `index.html` is the whole app. No libraries; the Excel file is built in plain JavaScript.
- `manifest.webmanifest` and `icons/` make it installable. `sw.js` saves the app files so it opens offline (network first, saved copy when offline).
- Hours are saved in the browser on that computer only. Each computer keeps its own hours (decided 2026-10-09: no syncing). Uninstalling the app or clearing that site's browser data deletes them, so save a shareable copy now and then as a backup.
- The page asks the browser to keep its storage ("persistent storage"), which installed apps in Chrome and Edge usually get.
- Font loads from Google Fonts and is saved for offline use after the first load. Without it, the system font is used.
- Icons are drawn by a small Pillow script (seven white bars, one per day, on the violet). The script was a one-off and isn't kept here; the PNGs are the source.

## Updating

Push to the `main` branch of `vwgp8wkgjz-beep/hours-log` on GitHub. Pages republishes in a minute or two. Installed apps pick up the new version the next time they open with internet. If you change the list of app files, bump `CACHE` in `sw.js`.

## Settings at the top of the script

- `WEEK_STARTS_MONDAY`: set to `false` for Sunday to Saturday weeks.
- `FULL_DAY`: hours that fill a day's bar (default 8).

## Built

2026-10-09. Design followed Anthropic's `frontend-design` skill (downloaded from `anthropics/claude-plugins-official`, not installed). Tested in a browser: entry, bad input, week totals, Excel export opened with openpyxl and LibreOffice, shareable copy in read-only mode, phone layout. Installable version tested the same day: offline helper registers, app files are cached, page opens with the server off and keeps its hours, shareable copy has no app links.

Checked before building the app version: Clockify (account needed, Excel export is paid), WorkingHours and HourLog (mainly Apple), Tie Tracker (desktop version unclear). None matched.

## Next, if wanted

- Import a shareable copy back in (restore from backup, or move hours to another computer).
- Multiple entries per day or per project.
