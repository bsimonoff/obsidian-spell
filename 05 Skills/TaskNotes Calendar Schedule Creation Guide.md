# TaskNotes Calendar Schedule Creation Guide

**Purpose:** Quick reference for creating calendar-integrated task schedules in Obsidian TaskNotes plugin without user intervention.

**Cross-reference**: See [[CLAUDE.md]] → "Calendar Schedule Creation (TaskNotes)" section for when to use this guide.

---

## CRITICAL REQUIREMENTS

### 1. YAML Frontmatter Structure
Each task **must be its own separate file** with proper frontmatter. No inline metadata.

**Required fields:**
```yaml
---
tags:
  - task
title: [Task Name]
status: pending
priority: [high/medium/low]
scheduled: [YYYY-MM-DDTHH:MM:SSZ]
timeEstimate: [minutes]
---
```

**Optional fields:**
- `projects`: "[[Project Name]]" for wiki links
- `contexts`: "@location" or "@situation"

### 2. Date/Time Formats (CRITICAL)

**Dates:** ISO 8601 format `YYYY-MM-DD`

**DateTime:** UTC ISO 8601 with `Z` suffix  
`YYYY-MM-DDTHH:MM:SSZ`

**Example:** `2026-07-14T15:00:00Z`

---

## TIME ZONE CONVERSION CHART

**Mountain Daylight Time (MDT) = UTC-6**

When converting local times to UTC:
- Add 6 hours to the local time
- Always append `Z` to indicate UTC

| Local Time | UTC Time |
|---|---|
| 7:00 AM | 13:00 UTC |
| 9:00 AM | 15:00 UTC |
| 1:00 PM | 19:00 UTC |
| 4:00 PM | 22:00 UTC |
| 5:00 PM | 23:00 UTC |

---

## DURATION FIELD (timeEstimate)

**Never use `due` field for end times.** This creates duplicate tasks at the end time.

**Use `timeEstimate` instead:**
- Value is in **minutes** (integer only)
- Extends the calendar block duration

**Common durations:**
- 1h 15m = 75 minutes (gym sessions)
- 3h = 180 minutes (work blocks)
- 1h = 60 minutes

---

## DATE CALCULATION

**When user asks for "Tuesday through Thursday":**

1. Get today's date: `Get-Date -Format "dddd, MMMM d, yyyy"`
2. Calculate the dates:
   - Tuesday = today + 1 day (if today is Monday)
   - Wednesday = today + 2 days
   - Thursday = today + 3 days

**DO NOT ASSUME DATES.** Always calculate from current date.

---

## WORKFLOW: Creating a Schedule

### Step 1: Confirm Current Date
```powershell
Get-Date -Format "dddd, MMMM d, yyyy"
```
Verify the day of the week and date.

### Step 2: Calculate Target Dates
- If Monday = Tue/Wed/Thu are +1, +2, +3 days
- Convert to YYYY-MM-DD format

### Step 3: Convert Times to UTC
- Assume Mountain Time (UTC-6) unless specified
- Local 7:00 AM = 13:00 UTC
- Local 9:00 AM = 15:00 UTC
- Local 1:00 PM = 19:00 UTC
- Local 4:00 PM = 22:00 UTC
- Add 6 hours to any local time for UTC

### Step 4: Create Individual Task Files
One file per task in `01 Journals/` folder.

**File naming:** `[Task Name] - [Day] [Date].md`

Example:
```
01 Journals/Gym Session - Tuesday July 14.md
01 Journals/FE Practice Exam - Tuesday July 14.md
```

### Step 5: Populate Frontmatter
```yaml
---
tags:
  - task
title: [Task Name]
status: pending
priority: high
scheduled: [UTC_DATETIME]
timeEstimate: [minutes]
---

[Description of task in body]
```

### Step 6: Verify No Duplicates
- Only `scheduled` + `timeEstimate` for timing
- NO `due` field (creates duplicate tasks)
- NO inline `⏰` timestamps (old format)

---

## COMMON MISTAKES & FIXES

| Mistake | Problem | Fix |
|---------|---------|-----|
| Using `due` field | Creates duplicate task at end time | Use `timeEstimate` only |
| Wrong time zone | Events show at wrong time | Add 6 hours for MDT (UTC-6) |
| Putting all tasks in one file | TaskNotes only reads single-task files | Create one file per task |
| Inline `⏰ 2026-07-14T07:00:00Z` | Not recognized by plugin | Use YAML frontmatter only |
| Using local times in `scheduled` | Times display incorrectly | Always use UTC with `Z` suffix |
| Forgetting `Z` on datetime | Ambiguous timezone | Always end with `Z` for UTC |

---

## STANDARD SCHEDULE TEMPLATE

For typical "balanced, avoid burnout" schedule (user with gym routine):

**Daily structure:**
- 7:00–8:15 AM: Gym (75 min)
- 9:00 AM–12:00 PM: Focus work (180 min)
- 1:00–4:00 PM: Different focus work (180 min)
- 4:00–5:00 PM: Admin/reflection (60 min)

**UTC equivalents (MDT):**
- Gym: 13:00–14:15 (13:00 start, 75 min duration)
- Morning block: 15:00–18:00 (15:00 start, 180 min duration)
- Afternoon block: 19:00–22:00 (19:00 start, 180 min duration)
- Reflection: 22:00–23:00 (22:00 start, 60 min duration)

---

## CHECKLIST: Before Presenting Schedule

- [ ] Current date verified with PowerShell
- [ ] All dates converted from day names to YYYY-MM-DD
- [ ] All times converted to UTC (add 6 for MDT)
- [ ] Each task has own file
- [ ] Only `scheduled` + `timeEstimate` in frontmatter
- [ ] No `due`, `⏰`, or inline metadata
- [ ] All files in `01 Journals/` folder
- [ ] File names include day and date
- [ ] `timeEstimate` in minutes (75, 180, 60, etc.)
- [ ] All datetimes end with `Z`

---

## REFERENCE: TaskNotes Documentation

- **Main:** https://tasknotes.dev/
- **Temporal Semantics:** https://tasknotes.dev/spec/03-temporal-semantics/
- **Task Properties:** https://tasknotes.dev/settings/task-properties/

Key insight: TaskNotes is frontmatter-first. All scheduling info lives in YAML, not markdown.

---

**Last Updated:** July 13, 2026  
**Status:** Verified with working implementation
