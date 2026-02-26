<div align="center">

# متقن — Mutqin

### نظام إدارة حياتك الشخصي | Personal Life Management System

**v2.1.0** · Single-File PWA · Arabic-First · Offline-Ready

[Live Demo](https://aelkelaany.github.io/Mutqin/) · [Report Bug](https://github.com/aelkelaany/Mutqin/issues)

</div>

---

## Overview

**Mutqin (متقن)** is a comprehensive personal life management application built as a single HTML file. It combines goal tracking, task management, expense tracking, meeting management, health tracking, prayer times, and personal notes into one portable, offline-capable progressive web app.

Designed for professionals who need a bilingual (Arabic/English) productivity system that works across devices without requiring any backend infrastructure or account creation.

---

## Features

### 🎯 Goals & Milestones

Hierarchical goal management with milestones and tasks. Each goal supports custom icons, colors, date ranges, and progress tracking. Milestones break goals into phases, and tasks within milestones can have priorities, statuses, dependencies, and repeat schedules. Progress is calculated automatically from task completion. Goals can be exported to Excel for management reporting.

### 🔥 Today View

A daily command center showing today's meetings, tasks (both goal-linked and quick tasks), and shopping/to-do lists. The Today tab is the default landing page. Adding new items from this view automatically pre-fills today's date. Meeting status badges (cancelled/deferred) are visible at a glance.

### 👥 Meetings

Dedicated meetings tab with four filter modes: All, Today, Upcoming, and Past. Each meeting supports title, date/time, location, attendees, agenda notes, meeting minutes, and decisions/action items. Meetings are grouped by month and searchable across all fields.

**Meeting Status** — Each meeting has a status selector with three options:
- **📅 Scheduled** — Default status for active meetings
- **❌ Cancelled** — Marks the meeting as cancelled with visual strikethrough
- **⏳ Deferred** — Requires entering a new date/time while automatically storing the original meeting datetime for reference

Deferred meetings show the original date as a reference badge, making it easy to track rescheduling history.

### 💰 Expense Tracking

Full-featured expense tracker with multi-currency support (SAR, USD, EUR, GBP, EGP, AED, KWD, BHD, QAR, OMR, JOD, TRY). Features include:

- **Budgets** with progress bars, spending limits, and close/freeze capability
- **Categories** with custom icons, colors, and monthly planned budget
- **Charts** — pie chart, bar chart by category, trend line, smart analysis
- **Budget Reports** with per-category breakdown and expandable transaction lists
- **Live Exchange Rates** with manual override option
- **Excel Export** with all fields (type, priority, next payment date, budget name, payment method)
- **Payment Method** tracking (cash, card, transfer)
- **Expense Type** — Fixed 🔒 or Variable 🔀
- **Priority** — Essential 🔴 / Comfort 🟡 / Luxury 🟢
- **Next Payment Date** — for tracking recurring due dates with 7-day alerts

**Budget: Include in Reports toggle** — Each budget has an `📊 Include in Reports` option. When turned OFF, its expenses are excluded from the Smart Analysis, monthly total card, and dashboard stats — useful for isolating one-time or project budgets from your regular spending view.

**📌 Recurring Fixed Expense Templates** — Tap the `📌` button in the expenses header to manage your fixed monthly expenses (rent, internet, subscriptions, etc.) as templates. Each template stores: description, amount, currency, category, priority, and payment method. At the start of each month, tap **"Import This Month"** to bulk-add all templates as new expense entries for the current date. Duplicate detection prevents re-importing the same title twice in the same month.

Closed budgets freeze their expenses from appearing in search results and summary statistics while preserving historical data for review.

### 💚 Health Tracker (NEW)

Comprehensive health monitoring system split into two layers:

**👤 Body Profile** (one-time setup, editable anytime):
- Height, target weight, age, gender
- Waist circumference and body fat % (monthly measurements)
- BMI auto-calculated with colored visual gauge (underweight → normal → overweight → obese)
- Weight gain/loss indicator from latest reading

**📋 Daily Log** (quick daily entry):
- ⚖️ Weight (with live BMI preview)
- 🩸 Blood Pressure (systolic/diastolic)
- 🔥 Calories consumed / burned
- 😴 Sleep hours
- 👣 Steps count
- 💧 Water intake (glasses)
- ☕ Caffeine (cups)
- 🕐 Fasting hours (intermittent/Ramadan)
- 🏋️ Workout duration + type (cardio/weights/walk/swim/cycling/treadmill)
- 😊 Mood (emoji selection)

**📊 Charts & Insights:**
- Weight trend line chart (30 days) with target weight goal line
- Steps bar chart (7 days)
- Sleep bar chart (7 days)
- Summary stats cards (7-day averages, today's water, blood pressure)

**📋 History:** Scrollable log of all entries, tap to edit any past entry.

### 🕌 Prayer Times (NEW)

Location-based prayer times displayed via a dedicated icon (🕌) in the header next to the weather widget. Tap to open a modal showing:

- **Fajr, Dhuhr, Asr, Maghrib, Isha** prayer times
- **Sunrise and Sunset** times
- **Next prayer** highlighted with a badge
- **Passed prayers** dimmed automatically

Uses the Aladhan API with Umm al-Qura calculation method (method 4). Falls back to Riyadh coordinates if geolocation is denied. Prayer data is fetched based on the user's current city via browser geolocation.

### 🔔 Smart Notifications (NEW)

Push notification system that works entirely client-side with no server required. Configure via the 🔔 bell icon in the header:

- **👥 Meeting Reminders** — configurable: 5, 10, 15, 30, or 60 minutes before
- **🕌 Prayer Reminders** — configurable: 5, 10, 15, or 30 minutes before next prayer
- **✅ Task Reminders** — morning notification at 8 AM listing today's pending tasks
- **💚 Health Log Reminder** — evening notification at 9 PM if no health data logged today
- **💾 Backup Reminder** — weekly reminder if no export has been made in 7+ days

Notifications use the browser Notification API and require one-time permission grant. Duplicate notifications are prevented using a 24-hour deduplication system.

### 📓 Notes (مفكرتي)

Four note types: Quick Note, Idea, Journal, and Important. Features include color-coded cards, pin to top, grid/list view toggle, and search. Note colors adapt between dark and light themes.

### 📊 Timeline

Visual timeline of all activities (tasks, meetings, expenses) plotted chronologically for a bird's-eye view of your productivity.

### 📅 Calendar

Hijri and Gregorian dual-calendar with dot indicators showing tasks, meetings, and expenses per day. Click any day to see all items and quickly add new ones with the date pre-filled.

### 📈 Statistics & Charts

Dashboard stats showing completed/active/pending tasks, completion percentage, and daily streak counter. Weekly bar chart visualizing task completion patterns.

---

## Technical Architecture

### Stack

| Layer | Technology |
|-------|-----------|
| **UI Framework** | React 18 (via Babel standalone) |
| **Styling** | CSS Variables + Tailwind utilities |
| **Storage** | IndexedDB (via inline wrapper) |
| **Export** | SheetJS (XLSX) |
| **Fonts** | Tajawal (Arabic) + Poppins (English) |
| **PWA** | Inline Service Worker + Web App Manifest |
| **Weather** | Open-Meteo API (free, no key required) |
| **Prayer Times** | Aladhan API (Umm al-Qura method) |

### Data Stores (IndexedDB)

```
goals, milestones, tasks, quickTasks, meetings,
expenses, categories, budgets, notes, taskLists, healthLogs
```

### Key Design Decisions

**Single-File Architecture** — The entire application (HTML, CSS, JS, icons, service worker, manifest) lives in one `goal-tracker.html` file (~2,170 lines). This makes deployment as simple as copying one file and enables hosting on GitHub Pages with zero build step.

**Offline-First** — The service worker caches all assets on first load. External API calls (weather, prayer times, exchange rates) are excluded from the cache and fail gracefully. All data persists in IndexedDB.

**No Authentication** — Data lives entirely on the user's device. Export/import via JSON backup provides portability.

**RTL-First** — The interface defaults to Arabic with full RTL support. English mode is available via a toggle in the header.

---

## Installation

### As a Website

Simply open the HTML file in any modern browser, or visit the [live demo](https://aelkelaany.github.io/Mutqin/).

### As a PWA (Recommended)

1. Open the app in Chrome or Safari
2. Click "Add to Home Screen" (or "Install App" on desktop)
3. The app installs as a standalone application with its own icon

### Self-Hosting

```bash
# Clone the repository
git clone https://github.com/aelkelaany/Mutqin.git

# Serve with any static server
cd Mutqin
python3 -m http.server 8000
# Open http://localhost:8000/goal-tracker.html
```

No build tools, no npm install, no environment variables required.

---

## Usage Guide

### Data Backup & Restore

The app shows a warning banner if no backup has been taken in 7+ days.

- **Export**: Settings icon → 💾 Export → saves a `.json` file with **all data**
- **Import**: Settings icon → 📥 Import → select a previously exported `.json` file
- **Excel Export**: Available per-goal (📤 button) and for filtered expenses (all fields)

**What the JSON backup includes:**

| Data | Source | Backed Up |
|------|--------|-----------|
| Goals, Milestones, Tasks | IndexedDB | ✅ |
| Quick Tasks, Task Lists | IndexedDB | ✅ |
| Meetings (incl. status/history) | IndexedDB | ✅ |
| Expenses (incl. type/priority/next-date) | IndexedDB | ✅ |
| Categories (incl. planned budget) | IndexedDB | ✅ |
| Budgets (incl. include-in-reports) | IndexedDB | ✅ |
| Notes | IndexedDB | ✅ |
| Health Logs | IndexedDB | ✅ |
| Health Body Profile | localStorage | ✅ |
| Exchange Rates + Base Currency | localStorage | ✅ |
| Recurring Expense Templates | localStorage | ✅ |
| Notification Settings | localStorage | ✅ |
| Theme + Language | localStorage | ✅ |

### Meeting Status Management

- When creating/editing a meeting, choose between **Scheduled**, **Cancelled**, or **Deferred**
- Selecting **Deferred** automatically saves the original date and prompts for a new date/time
- Cancelled meetings appear with strikethrough and reduced opacity
- Deferred meetings show the original date as a gold reference badge

### Health Tracking

- Tap **💚 Health** in the bottom navigation
- **First time:** Tap "Setup Profile" to enter height, target weight, age, and gender
- Use **"Log Today"** for quick daily entries (weight, BP, sleep, steps, water, etc.)
- BMI is auto-calculated and shown as a colored gauge in your Body Profile
- Update body measurements (waist, body fat %) monthly via the Profile edit button
- View weight trends over 30 days with your target weight as a goal line
- Track fasting windows (great for Ramadan or intermittent fasting)
- Log workout type and duration per session

### Budget Management

- Create budgets with a total amount, currency, and date range
- Assign expenses to budgets when adding them
- **Close a budget** (🔒) to freeze it — closed budgets hide their expenses from search and statistics, and prevent new expense entries. Reopen anytime from the edit modal.
- Budgets with existing expenses cannot be deleted (must remove expenses first or close the budget instead)

### Theme

Toggle between Dark Mode and Light Mode via the ☀️/🌙 button in the header. Both themes are carefully tuned for readability and visual comfort.

### Language

Toggle between Arabic and English via the `EN`/`عربي` button. The interface fully adapts including text direction (RTL/LTR).

---

## Keyboard Shortcuts & Gestures

| Action | Trigger |
|--------|---------|
| Navigate tabs | Tap bottom navigation bar |
| Expand/collapse goal | Tap goal card |
| Toggle task status | Tap status circle |
| Drag to reorder | Long press + drag (tasks/milestones) |
| Day details | Tap any calendar date |
| Prayer times | Tap 🕌 icon in header |

---

## Browser Support

| Browser | Status |
|---------|--------|
| Chrome (Desktop & Android) | ✅ Full support + PWA |
| Safari (iOS & macOS) | ✅ Full support + PWA |
| Firefox | ✅ Full support |
| Edge | ✅ Full support + PWA |
| Samsung Internet | ✅ Tested |

---

## Project Structure

```
Mutqin/
├── goal-tracker.html    # The entire application (single file)
├── README.md            # This file
└── .nojekyll            # GitHub Pages config
```

Inside `goal-tracker.html`:

```
Lines 1-30       → HTML head, meta tags, PWA manifest
Lines 31-56      → Inline Service Worker (cache: gt-v15)
Lines 57-200     → CSS (dark theme, light theme, components)
Lines 200-520    → Utility functions, IndexedDB, i18n
Lines 520-1060   → Components (StatsBar, Calendar, Dashboard, Today, MeetingsPage)
Lines 1060-1460  → Expense system (modals, charts, budgets)
Lines 1460-1650  → Notes system
Lines 1650-1925  → Health tracker (profile, daily log, BMI gauge, charts)
Lines 1925-2010  → Prayer times, LiveWidget
Lines 2010-2168  → App shell, routing, settings
```

---

## Version History

| Version | Cache | Changes |
|---------|-------|---------|
| gt-v16 | Current | 📌 Recurring expense templates, 📊 Budget "include in reports" toggle, 📤 Full-field Excel export (type/priority/next-payment/budget) |
| gt-v15 | — | 🔔 Notification system, Health tab restructured (body profile + daily log + charts), new metrics |
| gt-v14 | — | 💚 Health tracker, 🕌 Prayer times, Meeting status (scheduled/cancelled/deferred/done) |
| gt-v13 | — | Today default tab, budget close feature, delete protection, date pre-fill fix |
| gt-v12 | — | Light mode refinements, InfoBar removal |
| gt-v11 | — | Gold API fix, light mode color tuning |
| gt-v10 | — | CORS fix, light mode softening |
| gt-v9 | — | Meetings tab, calendar date fix, Excel export, meeting minutes |
| gt-v7 | — | Budget edit/delete in report view |
| gt-v6 | — | Notes system, reminders, Pomodoro timer |

---

## Author

**Ahmed Elkelaany**
Systems Analyst & Business Analyst
Ministry of Environment, Water and Agriculture — Saudi Arabia

---

## License

This project is personal software. All rights reserved.
