# 📋 Homework Tracker

A single-file, no-install homework tracker for teachers. Open it in a browser, set up your class once, and tick off homework as students complete it throughout the year — on a computer or a touchscreen. Progress autosaves automatically and exports to Excel whenever you need a report.

No server, no account, no dependencies to install. It's one `.html` file.

---

## ✨ Features

- **Quick setup** — paste your student list and homework list once and the tracker builds itself.
- **Name + surname support** — enter students as `First, Surname` to tell apart students who share a first name.
- **Tap-to-toggle grid** — tap any cell to mark homework done (✓, green) or not done (✗, red). Works with mouse and touch.
- **Homework activation toggle** — each homework column has its own switch (a small circle in the header) so you can add topics ahead of time and switch them on only once you actually assign them. Progress % is calculated only against homework that's been assigned — future/prepped topics don't drag scores down.
- **Live progress per student** — a percentage and progress bar per row, based on assigned homework only.
- **Grow the roster anytime** — add students or homework items mid-year; rename or delete either by double-clicking its label.
- **Autosave** — every tap is saved automatically in the browser (no "save" button needed to avoid losing progress).
- **Optional direct-to-disk autosave** — in Chrome or Edge on a computer, you can connect the tracker to a real file on your hard drive so it rewrites that file automatically, in addition to the browser's own storage.
- **Manual backup export** — download a dated snapshot of the whole tracker (roster + all progress) as a portable `.html` file you can move to another computer or keep as an archive.
- **Excel export** — exports a spreadsheet with `0 = done` and `1 = not done`, colour-coded cells, and Done / Assigned / % Complete columns, ready for `SUM` or `COUNTIF` formulas.
- **Everything stays on your device** — no data is ever sent to a server. It's just a local HTML file using your browser's storage.

---

## 🚀 Getting started

1. Download `homework_tracker.html` from this repository.
2. Open it by double-clicking the file (or dragging it into your browser).
3. On first launch you'll see the **setup screen**:
   - *Class name* (optional) — shown as the header of the student column.
   - *Students* — one per line. Add a surname after a comma if you like:
     ```
     John, Smith
     Mary, Jones
     Pepe, Ruiz
     ```
   - *Homework / topics* — one per line. You can always add more later.
4. Click **Create tracker**. Your table is built automatically.

---

## 🖱️ Using the tracker

| Action | How |
|---|---|
| Mark homework done / not done | Tap or click the cell |
| Activate / pause a homework column | Click the small circle in that column's header (✓ = assigned & counted, + = not yet assigned) |
| Rename or delete a student | Double-click their name |
| Rename or delete a homework item | Double-click its header label |
| Add a student | Click **+ Student** |
| Add a homework item | Click **+ Homework** (starts unassigned — activate it when you actually give it out) |
| Export a spreadsheet | Click **📊 Export Excel** |
| Download a backup copy | Click **💾 Save backup file** |
| Connect a file for automatic disk saving | Click **🔗 Connect file for autosave** (Chrome/Edge on a computer only) |
| Start over for a new school year | Click **Start new year** (clears the current roster/progress in this browser — back up first!) |

A line above the table always shows how many homework items are currently assigned out of the total you've created, so you know at a glance what's actively being tracked.

---

## 💾 How saving works (read this once)

This tracker has **three layers of saving**, so pick the combination that suits you:

1. **Automatic browser autosave (always on).** Every tap is saved instantly to your browser's local storage. Just keep using the same file/tab and it remembers everything — no action needed. ⚠️ This is tied to *this specific browser on this specific device*. If you clear browser data, switch browsers, or move to another computer, this copy is lost.
2. **Connected file autosave (optional, Chrome/Edge on desktop only).** Click **🔗 Connect file for autosave** once and pick (or create) a file on your computer. From then on, every change is written straight to that file on disk — a true, continuously updated physical copy. Not supported on Safari, Firefox, or most mobile browsers; the button will disable itself and tell you if it's unavailable.
3. **Manual backup export (works everywhere, anytime).** Click **💾 Save backup file** to download a dated `.html` snapshot containing your full roster and progress. Reopen that file anywhere — even with an empty browser — and it picks up exactly where you left off. Good practice: do this every week or two, and always right before switching computers or clearing browser data.

## 📊 Excel export

Exports one `.xlsx` file per class, with:
- One row per student, one column per homework item.
- `0` = homework done, `1` = homework not done — so a plain `SUM()` across a homework column tells you how many students still owe it.
- Homework columns not yet "assigned" export as blank cells and are labelled `(pending)`.
- `Done`, `Assigned`, and `% complete` summary columns per student.
- Colour-coded cells and a frozen header row for easy scanning.

---

## 🌐 Browser support

| Feature | Chrome / Edge (desktop) | Firefox / Safari | Mobile browsers |
|---|---|---|---|
| Core tracker (tap, export, backup) | ✅ | ✅ | ✅ |
| Browser autosave | ✅ | ✅ | ✅ |
| Direct-to-disk file autosave | ✅ | ❌ | ❌ (varies by device/browser) |

If direct-to-disk autosave isn't available, the tracker still works fully — just rely on browser autosave day-to-day and download a backup file periodically.

---

## 🔒 Privacy

Everything runs entirely in your browser. There is no backend, no account, and no data is uploaded anywhere. Your roster and homework records live only in your browser's local storage and in whatever `.html`/`.xlsx` files you choose to save.

---

## 🛠️ Tech notes

- Single self-contained HTML file — no build step, no npm install.
- Uses [`xlsx-js-style`](https://github.com/gitbrent/xlsx-js-style) (loaded from a CDN) for styled Excel export.
- Uses the browser's [File System Access API](https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API) for optional direct-to-disk autosave.
- State (roster, homework list, records, assignment status) is stored as JSON, both in `localStorage` and embedded directly into any exported/backup `.html` file for portability.
