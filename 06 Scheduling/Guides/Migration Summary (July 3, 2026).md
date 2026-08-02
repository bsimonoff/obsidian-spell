# 06 Scheduling Migration Summary
**Date:** July 3, 2026  
**Status:** ✅ Complete

---

## What Was Done

### 1. ✅ Replaced `06 Schedule` Folder
**Old structure (static):**
- Weekly Schedule Overview
- Daily Habit Schedule (templates)
- Calendar views (manual)
- Quick reference cards

**New structure (dynamic):**
- Individual task files with YAML metadata
- Three custom Views (Kanban, List, Calendar)
- Real-time tracking and filtering
- Single source of truth

**Result:** Deleted `06 Schedule` entirely. All content migrated to 06 Scheduling format.

---

## New 06 Scheduling Structure

### 📁 Files Created

#### Main Documents
- **[[Job Search & Life Tracking System]]** — Full documentation with embedded Views
- **[[⚡ Quick Start Guide]]** — Setup instructions and templates
- **[[Migration Summary (July 3, 2026)]]** — This file

#### Example Tasks (Seeds)
- **Research Valero Energy process engineer roles** — Job search task example
- **Create speedpaint for Sunday TikTok post** — Art task example
- **Submit 5 job applications - July 4** — Daily habit task example

#### Custom Views (Bases)
| View | Purpose | Access |
|------|---------|--------|
| `job-search-board.base` | Application pipeline (Kanban) | Filter by status, company, salary |
| `art-growth.base` | Art posts & engagement | Filter by platform, status, date |
| `daily-habits.base` | Daily quota tracking | Filter by category, date, status |

#### Default Views (From 06 Scheduling Plugin)
- `tasks-default.base` — Master task list with multiple views
- `calendar-default.base` — Full calendar view
- `agenda-default.base` — Timeline/agenda view
- `kanban-default.base` — Generic Kanban board
- `mini-calendar-default.base` — Compact calendar
- `pomodoro-stats.base` — Time tracking stats
- `relationships.base` — Task relationships/dependencies

---

## What This Means for You

### Before (Old System)
- ❌ Weekly schedule was a static document
- ❌ Daily templates required manual copying
- ❌ No calendar integration
- ❌ Manually typed tracker updates
- ❌ Procrastination → "forgot to update"

### After (06 Scheduling System)
- ✅ Weekly plan = collection of tasks with `scheduled` dates
- ✅ Daily templates = task files you can duplicate
- ✅ Calendar automatically shows scheduled dates
- ✅ Status moves from "open" → "in-progress" → "done"
- ✅ Views auto-calculate week summaries, streaks, engagement

---

## How to Use (3 Steps)

### Step 1: Open the Task View
Command palette → `06 Scheduling: Open tasks view`

You'll see:
- **Job Search Board** (Kanban)
- **Art Growth** (tracking)
- **Daily Habits** (quota)

### Step 2: Create Tasks
Command palette → `06 Scheduling: Create new task`

Example: `Apply to Chevron Process Engineer role #job-search`

Edit the task file to add properties:
```yaml
priority: high
scheduled: 2026-07-04
company: Chevron
salary: 80000
```

### Step 3: Review Weekly
Every Sunday evening:
1. Open task view
2. Count this week's applications, posts, habits
3. Move completed tasks to "done"
4. Create next week's tasks

---

## The Four Task Types

### 1. Job Search Tasks (⬛ High Priority)
**Properties:**
- `company`, `role`, `salary`, `location`, `source`, `contact`
- `priority: high` (always)
- `scheduled: [your research date]`
- `dueDate: [application deadline]`

**Example:** `Research Valero Energy process engineer roles`  
**Tag:** `#job-search`

### 2. Art Tasks (🎨 Creative)
**Properties:**
- `platform`, `postType` (speedpaint, finished piece, WIP)
- `engagement`, `followerCount`
- `scheduled: [when you'll create it]`

**Example:** `Create speedpaint for Sunday TikTok post`  
**Tag:** `#art`

### 3. Daily Habit Tasks (📋 Routine)
**Properties:**
- `category` (job-applications, gym, sleep, planning)
- `scheduled: [today's date]`
- `dueDate: [end of day]`

**Example:** `Submit 5+ job applications - July 4`  
**Tag:** `#habit`

### 4. Planning Tasks (🎯 Meta)
**Properties:**
- `category: planning`
- `scheduled: [every Sunday evening]`
- `priority: normal`

**Example:** `Weekly review and planning - Week of July 7`  
**Tag:** `#planning`

---

## Calendar Integration

Every task with a `scheduled` date appears on Obsidian's calendar.

**Use this to:**
- See all events/tasks at once (interviews, art deadlines, application quotas)
- Time-block your week ("This week I have 3 interviews + 2 art posts")
- Plan ahead ("August looks light on applications, good time for negotiation")

Click a date on the calendar to see all tasks scheduled that day.

---

## Weekly Review Checklist

**Every Sunday, 15 minutes:**

- [ ] Open Task View
- [ ] Review "This Week" in Job Search Board
  - How many applications submitted? (goal: 20-25)
  - Any interviews scheduled? When?
  - Any companies to follow up with?
- [ ] Review "Posted" in Art Growth
  - How many posts? (goal: 2-3)
  - Best engagement?
- [ ] Review "Completion Status" in Daily Habits
  - Gym days: ___ / 7
  - Applications: ___ / 25-30
  - Art posts: ___ / 3
  - Sleep consistency: ___ nights 7+ hours
- [ ] Move completed tasks to "done" status
- [ ] Create next week's daily tasks
  - Duplicate "Submit 5 job applications" template 5 times (Mon-Fri)
  - Create art tasks for Sun/Wed/Sat
  - Create planning task for next Sunday

---

## Commands Cheat Sheet

| What You Want | Command |
|---------------|---------|
| Create a new task | `06 Scheduling: Create new task` |
| Open task command center | `06 Scheduling: Open tasks view` |
| Edit task properties | Right-click task link → **Edit properties** |
| Regenerate default views | `06 Scheduling: Create files` |
| Search all tasks | `06 Scheduling: Search` |
| Archive old tasks | Move to status "done" |

---

## Data Migration

**What was preserved:**
- Weekly time allocation (15-20 hrs job search, 5-8 hrs art, etc.) → encoded in task priorities and scheduled dates
- Daily routine (morning/afternoon/evening blocks) → task descriptions with time slots
- Art posting schedule (Sun/Wed/Sat) → art task calendar dates
- Habit tracking (gym, sleep, applications) → daily habit tasks

**What changed:**
- Format: Documents → Tasks (YAML metadata)
- Updates: Manual → Automatic (views auto-calculate summaries)
- Tracking: "Did I do this?" → Clear status tracking

---

## Migration Validation

**Files deleted:**
- ✅ `06 Schedule/Weekly Schedule Overview.md`
- ✅ `06 Schedule/Daily Habit Schedule (Task Notes).md`
- ✅ `06 Schedule/Quick Daily Schedule Card.md`
- ✅ `06 Schedule/Weekly Habit Tracker.md`
- ✅ `06 Schedule/How to Use Task Notes Plugin.md`
- ✅ `06 Schedule/Quick Reference Card.md`
- ✅ `06 Schedule/July 2026 Calendar.md`
- ✅ `06 Schedule/Daily Schedule - Task Notes Minimal.md`
- ✅ `06 Schedule/Daily Calendar Template.md`
- ✅ Full folder: `06 Schedule/` deleted

**Files created:**
- ✅ 3 custom View files (`.base`)
- ✅ 3 example tasks (seeding the system)
- ✅ 2 documentation files
- ✅ 1 summary (this file)

---

## Next Actions (In Order)

1. **Today:** Read [[⚡ Quick Start Guide]]
2. **Today:** Enable Bases plugin in Obsidian Settings
3. **Today:** Open task view and explore the example tasks
4. **Tomorrow:** Create your first 3 job search tasks (target companies)
5. **Friday:** Create daily application tasks for next week (batch job)
6. **Sunday:** Do first weekly review (15 min)

---

## Pro Tips

**Batch create:** On Sunday, create all of next week's tasks at once:
- 5 daily application tasks (Mon-Fri)
- 3 art creation tasks (Sun/Wed/Sat)
- 1 planning task (next Sunday)

**Duplicate tasks:** Right-click a task file → **Duplicate** to copy templates quickly

**Scheduled vs Due:** 
- `scheduled: 2026-07-04` = when you'll *do* it
- `dueDate: 2026-07-07` = when it's *due* (e.g., application deadline)

**Color coding:** In 06 Scheduling settings, assign colors to tags for visual organization in the task view

---

## Questions?

Refer to:
- **Setup & quick start:** [[⚡ Quick Start Guide]]
- **Full documentation:** [[Job Search & Life Tracking System]]
- **Official 06 Scheduling docs:** [tasknotes.dev](https://tasknotes.dev)

---

**Status:** ✅ Ready to use  
**Last updated:** July 3, 2026  
**Created by:** Claude (Claudian)
