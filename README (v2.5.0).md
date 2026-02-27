<div align="center">

# متقن — Mutqin

### نظام إدارة حياتك الشخصي | Personal Life Management System

**v2.5.0** · Single-File PWA · Arabic-First · Offline-Ready

[Live Demo](https://aelkelaany.github.io/Mutqin/) · [Report Bug](https://github.com/aelkelaany/Mutqin/issues)

</div>

---

## Overview

**Mutqin (متقن)** is a comprehensive personal life management application built as a single HTML file. It combines goal tracking, task management, full financial tracking (expenses + income), meeting management, health tracking, prayer times, and personal notes into one portable, offline-capable progressive web app.

Designed for professionals who need a bilingual (Arabic/English) productivity system that works across devices without any backend infrastructure or account creation.

---

## What's New in v2.5.0

| # | Feature | Description |
|---|---------|-------------|
| 1 | 📥 **Income Tracking** | Full income system with separate categories (Salary, Cashback, Transfer, Freelance, Gift, Other) |
| 2 | 💰 **Effective Budget Model** | Income linked to a budget increases its effective limit — original plan stays intact |
| 3 | 📊 **Income/Expense Summary** | Monthly dashboard shows expenses vs income + net balance |
| 4 | 🏷️ **Income Categories** | Add/edit custom income categories via ⚙️ management mode |
| 5 | ⏱️ **Meeting Time Badges** | All meetings show relative time (منذ يوم، بعد 3 ساعات، أمس…) with color coding |
| 6 | 🍅 **Pomodoro Fix** | Timer never drifts or stops when switching apps — uses absolute timestamps |
| 7 | 🔧 **Currency Select Fix** | RTL overlap between currency text and dropdown arrow resolved |

---

## Features

### 🎯 Goals & Milestones

Hierarchical goal management with milestones and tasks. Each goal supports custom icons, colors, date ranges, and progress tracking. Milestones break goals into phases; tasks support priorities, statuses, dependencies, and repeat schedules. Goals export to Excel.

### 🔥 Today View

Daily command center showing today's meetings, tasks, and to-do lists. Default landing tab. Adding items pre-fills today's date automatically.

### 👥 Meetings

Four filter modes: All, Today, Upcoming, Past. Each meeting supports title, date/time, location, attendees, meeting minutes, and decisions. Grouped by month, searchable across all fields.

**Smart Relative Time Badges** — Every meeting shows a live time badge:

| Time | Arabic | English |
|------|--------|---------|
| < 1 hour away | `بعد 25 دقيقة` | `in 25m` |
| Same day | `بعد 3 ساعة` | `in 3h` |
| Next calendar day | `غداً` | `Tomorrow` |
| This week | `بعد 5 أيام` | `in 5 days` |
| Yesterday | `أمس` | `Yesterday` |
| Recent past | `منذ 3 أيام` | `3d ago` |
| Older | `منذ 2 أسابيع` | `2w ago` |
| Much older | `منذ 3 أشهر` | `3mo ago` |

Color coding: 🟦 Teal = upcoming · 🔴 Red = passed · ⬜ Gray = done

**Meeting Status:** Scheduled 📅 · Done ✅ · Cancelled ❌ · Deferred ⏳

Deferred meetings retain the original date as a gold reference badge.

### 💰 Financial Tracking — Expenses + Income

Full-featured financial tracker with multi-currency support.

#### Transactions (📤 Expense / 📥 Income)

A single modal with a toggle at the top switches between Expense and Income mode. The active type determines which categories are shown, which fields appear, and how amounts are color-coded (red for expenses, green for income).

**Expense fields:** Category, Amount, Currency, Date, Payment Method (Cash/Card/Transfer), Type (Fixed/Variable), Priority (Essential/Comfort/Luxury), Next Payment Date, Budget link, Notes

**Income fields:** Income Category, Amount, Currency, Date, Payment Method, Budget link, Notes

#### Income Categories (Built-in)

| Icon | Arabic | English |
|------|--------|---------|
| 💼 | راتب | Salary |
| 💰 | كاش باك | Cashback |
| 🏦 | تحويل وارد | Transfer In |
| 🤝 | عمل حر | Freelance |
| 🎁 | هدية | Gift |
| 📥 | إيراد أخرى | Other Income |

Custom income categories can be added from Settings ⚙️ → Income Categories.

#### Effective Budget Model

When income is linked to a budget:

```
Effective Budget = Base Budget Amount + Linked Income
Remaining        = Effective Budget − Expenses
```

The original `totalAmount` is never modified. Income is stored as transactions and computed at runtime. This preserves the planning baseline while reflecting real cash flow.

Example display in budget detail:
```
📥 إيرادات: 1,500 SAR  ←  ميزانية فعلية: 6,500 SAR
```

#### Monthly Summary Dashboard

```
┌─────────────────────┬─────────────────────┐
│ 📤 مصاريف الشهر    │ 📥 إيرادات الشهر   │
│    3,200 SAR         │    5,000 SAR         │
│                      │  ↑ 1,800 (صافي)     │
└─────────────────────┴─────────────────────┘
```

#### Charts & Analytics

- Pie chart by category (expenses only)
- Monthly bar chart (6 months)
- Trend line
- Category table with percentages
- Smart analysis (priority breakdown, planned vs actual, upcoming payments)
- All charts exclude closed budgets and budgets marked "exclude from reports"
- Income transactions excluded from expense charts

#### Export

- **📤 Excel** — per-budget transactions with exchange rates and category summary sheet
- **📄 PDF Report** — dark-themed analytical report with KPI cards, charts, and full transaction table. Opens in browser → 🖨️ → Save as PDF

### 🏷️ Category Management (⚙️ Mode)

Categories split into two sections:

**📤 Expense Categories** — custom icon, color, monthly planned budget limit
**📥 Income Categories** — custom icon, color (no budget limit field)

Both support Arabic + English names and 80+ icon options. The Category modal has a type toggle at the top (Expense / Income).

### 🍅 Pomodoro Timer (Background-Accurate)

The timer stores an absolute end timestamp (`Date.now() + remaining × 1000`) when started. Every 500ms it reads `Date.now()` to compute remaining time — it **never drifts** regardless of tab switching, phone lock screen, or browser throttling. On returning to the tab, `visibilitychange` triggers an immediate recalculation.

- Work: 25 min → Short Break: 5 min → Long Break: 15 min (every 4 sessions)
- Floating mini button shows live countdown when panel is closed
- Audio bell on session completion

### 💚 Health Tracker

**👤 Body Profile:** Height, weight target, age, gender, waist, body fat %. BMI gauge auto-calculated.

**📋 Daily Log:** Weight · Blood Pressure · Calories · Sleep · Steps · Water · Caffeine · Fasting · Workout · Mood

**📊 Charts:** Weight trend 30d, Steps 7d, Sleep 7d, summary stat cards.

### 🕌 Prayer Times

Location-based Fajr, Dhuhr, Asr, Maghrib, Isha + Sunrise/Sunset. Next prayer highlighted, passed prayers dimmed. Aladhan API, Umm al-Qura method. Tap 🕌 in header.

### 🔔 Smart Notifications

- Meeting reminders: 5/10/15/30/60 min before
- Prayer reminders: 5/10/15/30 min before
- Task reminder: 8 AM daily
- Health log reminder: 9 PM if nothing logged
- Backup reminder: weekly

### 📓 Notes

Quick Note, Idea, Journal, Important. Colored cards, pin-to-top, grid/list toggle, full-text search.

### 📅 Calendar

Hijri + Gregorian dual-calendar. Dot indicators for tasks, meetings, expenses per day. Tap any day for details + quick-add with date pre-filled.

### 📊 Statistics

Completed/active/pending task counts, completion %, daily streak, weekly bar chart.

---

## Technical Architecture

### Stack

| Layer | Technology |
|-------|-----------|
| UI Framework | React 18 (Babel standalone, no build step) |
| Styling | CSS custom properties + utility classes |
| Storage | IndexedDB (inline async wrapper) |
| Export | SheetJS (XLSX) + Browser Print API (PDF) |
| Fonts | IBM Plex Sans Arabic (Google Fonts CDN) |
| PWA | Inline Service Worker + Web App Manifest |
| Weather | Open-Meteo API (no key required) |
| Prayer Times | Aladhan API (Umm al-Qura, method 4) |
| Exchange Rates | Open Exchange Rates + manual override |

### Data Stores (IndexedDB)

```
goals · milestones · tasks · quickTasks · meetings
expenses · categories · budgets · notes · taskLists · healthLogs
```

### Key Design Decisions

**Single-File Architecture** — HTML + CSS + JS + Service Worker + Manifest in one `index.html` (~3,500 lines). Deploy by copying one file.

**Income/Expense Separation** — Income stored as `expenses` records with `txType: 'income'`. Effective budget computed at runtime. Original `totalAmount` never mutated. Analytics queries filter by `txType` to keep expense charts clean.

**Pomodoro Accuracy** — `endTimeRef = Date.now() + timeLeft * 1000` stored on start. Ticks read `Date.now()` instead of decrementing. `visibilitychange` listener recalibrates on tab return.

**Offline-First** — Service worker caches all local assets. APIs fail gracefully. All data in IndexedDB.

**No Auth** — Device-local data. JSON export/import for portability.

**RTL-First** — Arabic default, full RTL layout. EN/عربي toggle in header.

---

## Installation

### Browser (Simplest)
Open `index.html` in any modern browser, or visit the [live demo](https://aelkelaany.github.io/Mutqin/).

### PWA Install (Recommended)
1. Open in Chrome or Safari
2. Tap **"Add to Home Screen"** / **"Install App"**
3. Launches as standalone app with its own icon

### Self-Hosting
```bash
git clone https://github.com/aelkelaany/Mutqin.git
cd Mutqin
python3 -m http.server 8000
# Open http://localhost:8000/index.html
```

No build tools. No npm. No environment variables.

---

## Usage Guide

### Adding Income
1. Go to **💰 المعاملات** tab
2. Tap **📥 إيراد** button (next to 📤 مصروف)
3. Select an income category
4. Optionally link to a budget — the effective budget increases automatically

### Managing Income Categories
1. Tap **⚙️** in the Transactions header
2. Scroll to **📥 تصنيفات الإيرادات**
3. Tap **+ جديد** to add a custom category
4. The Category modal opens pre-set to Income type

### PDF Budget Report
1. **💰 Transactions** → Charts tab → Budgets section
2. Select a budget
3. Tap **📄 تقرير PDF**
4. New window opens → tap 🖨️ → Save as PDF

### Pomodoro (Background-Safe)
Start a session then switch apps freely. Return to the tab at any time — the timer shows the correct remaining time instantly.

### Meeting Time Badges
Appear automatically on all non-cancelled meetings. No setup required. Updated on each render.

### Data Backup & Restore
- **Export** — Settings → 💾 Export → `.json` file (all data)
- **Import** — Settings → 📥 Import → select `.json` file
- **Excel** — per-budget and all-expenses export available

### Budget Management
1. Create a budget with base amount, currency, date range
2. Add expense transactions linked to the budget
3. Add income transactions linked to the budget to raise the effective limit
4. **Close** (🔒) to freeze — excluded from analytics, no new entries allowed
5. **Exclude from Reports** — exists in DB but hidden from charts

---

## Browser Support

| Browser | Support |
|---------|---------|
| Chrome (Desktop & Android) | ✅ Full + PWA |
| Safari (iOS & macOS) | ✅ Full + PWA |
| Firefox | ✅ Full |
| Edge | ✅ Full + PWA |
| Samsung Internet | ✅ Tested |

---

## Project Structure

```
Mutqin/
├── index.html    # Entire application (~3,500 lines)
├── README.md     # This file
└── .nojekyll     # GitHub Pages config
```

---

## Version History

| Version | Highlights |
|---------|-----------|
| **v2.5.0** | 📥 Income tracking + categories, effective budget model, monthly income/expense dashboard, meeting relative time badges (all statuses + past months), Pomodoro background-accuracy fix, category modal type toggle, select RTL overlap fix |
| v2.4.0 | 📄 PDF budget report, analytics exclude closed/hidden budgets, dual export buttons (Excel + PDF) |
| v2.3.0 | 📌 Recurring expense templates in BudgetModal, currency conversion on import |
| v2.2.0 | Expense type (fixed/variable), priority levels, next payment date, category planned budgets, smart analysis, proactive alerts |
| v2.1.0 | 🔔 Notification system, 💚 Health tab restructure, budget close feature |
| v2.0.0 | 💚 Health tracker, 🕌 Prayer times, meeting status system |
| v1.9.0 | Today default tab, budget close, delete protection |
| v1.5.0 | 📓 Notes, 🍅 Pomodoro, meeting minutes & decisions |
| v1.0.0 | Initial release — Goals, Tasks, Meetings, Expenses, Calendar |

---

## Author

**Ahmed Elkelaany**  
Systems Analyst & Business Analyst  
Ministry of Environment, Water and Agriculture — Saudi Arabia

---

## License

This project is personal software. All rights reserved.
