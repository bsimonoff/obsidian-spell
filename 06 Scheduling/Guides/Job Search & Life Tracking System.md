# 06 Scheduling Job Search & Life Tracking System

This is your command center for landing a $70k+ job by September 30, 2026. Everything here is task-based and calendar-aware.

## System Overview

**Three tracking bases:**
1. **Job Search Tasks** — Applications, research, outreach, interviews
2. **Art & Growth Tasks** — Content creation, posting, engagement
3. **Habits & Daily Work** — Gym, sleep, applications quota, weekly planning

All tasks are stored as individual Markdown notes with YAML metadata. Views (Bases) provide different visualizations: calendar, list, agenda, kanban.

---

## Core Properties for All Tasks

Every task has:
- `status` — open, in-progress, done
- `priority` — high, normal, low
- `scheduled` — when you plan to do it
- `dueDate` — when it's due
- `tags` — for categorization
- `dateCreated` / `dateModified` — automatic

**Custom properties by task type:**
- **Job Search:** `company`, `role`, `salary`, `source`, `contact`
- **Art:** `platform`, `postType`, `engagement`, `followerCount`
- **Habits:** `category` (gym, sleep, applications, planning)

---

## How to Use

### 1. Create a Task (Daily)

From command palette: `06 Scheduling: Create new task`

**Job search example:**
```
Research Chemical Engineering roles at Valero Energy #job-search #valero
```

**Art example:**
```
Create speedpaint for TikTok post Sun 7-9pm #art #tiktok
```

**Habit example:**
```
Complete 5 job applications today #habit #job-applications
```

After saving, 06 Scheduling creates a `.md` file. Add custom properties in the YAML:

```yaml
status: open
priority: high
scheduled: 2026-07-04
company: Valero Energy
role: Process Engineer
salary: 75000
source: LinkedIn
```

### 2. Views (Bases) to Use

#### **Job Search Board (Kanban)**
- See all job applications by status: **Open → In Progress → Interviewed → Offered**
- Drag tasks to move them
- Click a task to edit company, role, salary

#### **This Week's Tasks (Agenda)**
- Calendar view of what's due/scheduled this week
- Plan your day around deadlines and interviews

#### **Job Search + Art Calendar**
- See applications, interviews, art posting schedule on one calendar
- Color-coded by type

#### **Daily Habit Tracker (List)**
- Quick checkbox view: Did you gym today? 5 applications done? Art posted?
- Filter by week

#### **Art Growth (List)**
- Track posts, platforms, engagement metrics
- Sort by engagement or date posted

### 3. Weekly Review (Sunday Evening)

Each week, review:
- **Job applications submitted:** Check your "Applications This Week" list
- **Interviews scheduled:** Filter tasks by status "interviewed" for upcoming ones
- **Art posts published:** Check "Art Posts This Week"
- **Habit streak:** Gym days, sleep consistency, app quota met

---

## Task Template Examples

### Job Search Task
```markdown
---
status: open
priority: high
scheduled: 2026-07-04
dueDate: 2026-07-07
company: Valero Energy
role: Process Engineer (Junior)
salary: 75000
location: Houston, TX
source: LinkedIn
contact: jane.smith@valero.com
tags:
  - job-search
  - chemical-engineering
  - houston
---

# Research Chemical Engineering roles at Valero Energy

## Company Info
- Industry: Energy, Oil & Gas
- Size: Large (50k+ employees)
- Culture notes: [research and add]

## Role Details
- Job link: [add]
- Requirements: [add]

## Action Items
- [ ] Read full job description
- [ ] Identify 3 key qualifications I have
- [ ] Draft tailored cover letter
- [ ] Submit application
- [ ] Follow up in 1 week
```

### Art Creation Task
```markdown
---
status: open
priority: normal
scheduled: 2026-07-06
dueDate: 2026-07-06
tags:
  - art
  - tiktok
platform: TikTok
postType: speedpaint
---

# Create speedpaint for Sunday TikTok post

Time: 7:00-8:30pm  
Medium: Digital (Procreate or Clip Studio Paint)  
Theme: [character design / landscape / fan art]

## Checklist
- [ ] Plan composition (2 min)
- [ ] Sketch/base (10 min)
- [ ] Color/render (20 min)
- [ ] Details/polish (10 min)
- [ ] Export as video (5 min)
- [ ] Write caption with hashtags
- [ ] Post to TikTok
- [ ] Share to Instagram Reels

Expected engagement: [if this is a follow-up to previous post]
```

### Daily Habit Task
```markdown
---
status: open
priority: high
scheduled: 2026-07-04
dueDate: 2026-07-04
tags:
  - habit
  - daily
category: job-applications
---

# Submit 5 job applications today (July 4)

## Morning (8:30am - 12:00pm)
- [ ] Application 1: [Company Name]
- [ ] Application 2: [Company Name]
- [ ] Break

## Afternoon (1:00pm - 5:00pm)
- [ ] Application 3: [Company Name]
- [ ] Application 4: [Company Name]
- [ ] LinkedIn outreach (2 messages)

## Evening (5:00pm - 6:00pm)
- [ ] Update Application Tracker
- [ ] Log companies researched

**Goal:** 5+ applications by 5:00pm  
**Status:** ⬜ Not started / 🟨 In progress / ✅ Complete
```

---

## Views to Embed in Notes

### Job Search Command Center

**Application Pipeline (Kanban board - drag tasks to move through stages):**
![[job-search-board.base]]

### Art & Growth Tracking

**Art Posts & Engagement:**
![[art-growth.base]]

### Daily Habits & Quota Tracking

**Daily Habits by Status:**
![[daily-habits.base]]

---

## Migration from 06 Schedule

Old structure (07/06):
- Weekly Schedule Overview → Weekly planning task (Sundays)
- Daily Habit Schedule → Daily task templates
- Calendar → 06 Scheduling calendar view
- Art posting schedule → Individual art creation tasks

All consolidated into 06 Scheduling for a single source of truth.

---

## Key Rules

✅ **DO:**
- Create a task for anything that needs a deadline or calendar slot
- Use `priority: high` for job applications (time-sensitive)
- Tag everything (#job-search, #art, #habit)
- Schedule tasks when you'll do them (not just due date)
- Update task status daily

❌ **DON'T:**
- Mix tasks with notes (tasks are actions, notes are reference)
- Leave a task without a scheduled date
- Skip weekly review (every Sunday, 15 min)
- Let old completed tasks pile up (archive them monthly)

---

## Quick Start Checklist

- [ ] Enable Obsidian **Bases** core plugin (Settings → Core plugins)
- [ ] Review this document (you're reading it!)
- [ ] Create your first task: "Apply to 3 companies today" with priority high
- [ ] Set up calendar view in this note
- [ ] Create Sunday weekly planning task (recurring)
- [ ] Delete or archive 06 Schedule folder

---

**Your job search runs on momentum. Tasks keep that momentum visible.**

*Last updated: July 3, 2026*
