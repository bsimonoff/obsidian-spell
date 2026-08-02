# ⚡ Quick Start: 06 Scheduling Job Search System

Everything you had in `06 Schedule` is now **task-based, calendar-aware, and trackable in real-time.**

## What Changed
✅ **Old:** `06 Schedule` folder (static documents)  
✅ **New:** `06 Scheduling` system (dynamic, queryable tasks)

**Benefits:**
- Calendar view shows applications, interviews, and art posts together
- Drag tasks to track progress (Open → In Progress → Done)
- Filter by company, role, platform, or due date instantly
- Weekly review takes 5 minutes (not 30)
- No context switching between multiple documents

---

## Your First Steps (Do These Today)

### 1. ✅ Enable the Bases Plugin
- Open Obsidian Settings
- Go to **Core plugins**
- Enable **Bases** (search for it if hidden)
- Reload Obsidian

### 2. 📋 Open the Task Views
From command palette: `06 Scheduling: Open tasks view`

You'll see three tabs:
- **Job Search Board** — Your application pipeline (Kanban)
- **Art Growth** — Posts and engagement tracking
- **Daily Habits** — Your daily quota checklist

### 3. 🎯 Create Your First Task
From command palette: `06 Scheduling: Create new task`

**Example:**
```
Apply to Chevron Process Engineer role #job-search #houston
```

After saving, open the task note and add:
```yaml
priority: high
scheduled: 2026-07-04
dueDate: 2026-07-07
company: Chevron
role: Process Engineer
salary: 80000
location: Houston, TX
source: LinkedIn
```

The task now appears in your Job Search Board **automatically**.

### 4. 📅 Review This Week's Tasks
In `06 Scheduling/Views/job-search-board.base`, switch to **"This Week"** tab to see what's due soon.

### 5. 🔄 Sunday Evening Review (15 min)
Every Sunday:
- Open the Task View (command palette)
- Count applications submitted this week
- Count art posts created
- Check habit streaks (gym, sleep, quota)
- Move completed tasks to "done" status
- Create tasks for next week

---

## Task Templates (Copy & Paste)

### Job Search Task
```markdown
---
status: open
priority: high
scheduled: 2026-07-04
dueDate: 2026-07-07
company: [Company Name]
role: [Role Title]
salary: [Estimated Salary]
location: [City, State]
source: [LinkedIn/Indeed/Recruiter/etc]
contact: [Hiring Manager Email if known]
tags:
  - job-search
  - chemical-engineering
  - [city-name]
---

# [Company Name] - [Role Title]

## Company Info
- [Research notes]

## Action Items
- [ ] Read job description
- [ ] Find hiring manager
- [ ] Draft cover letter
- [ ] Submit application
- [ ] Follow up in 1 week
```

### Art Task
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

# [Art Title] - Sunday TikTok Post

- [ ] Create art
- [ ] Export video
- [ ] Write caption
- [ ] Post to TikTok
- [ ] Copy to Instagram
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

# Submit 5+ applications - [Date]

- [ ] Application 1
- [ ] Application 2
- [ ] Application 3
- [ ] Application 4
- [ ] Application 5
- [ ] LinkedIn outreach
- [ ] Update tracker
```

---

## Pro Tips

**Drag to move:** Click a task in the Kanban board and drag it to a different column (Open → In Progress → Done)

**Batch create:** Create all week's daily tasks on Sunday (5 job app tasks Mon-Fri, 3 art tasks Sun/Wed/Sat)

**Weekly template:** Copy the daily habit task template 5 times for the upcoming week

**Calendar integration:** The `scheduled` date shows up on Obsidian's calendar — use this to block time for interviews or art creation

**Custom properties:** You can add more properties (like `interviewDate`, `engagementCount`, `energyLevel`) — they'll show up in task notes automatically

---

## Common Commands

| Command | What It Does |
|---------|--------------|
| `06 Scheduling: Create new task` | New task from scratch |
| `06 Scheduling: Open tasks view` | Open the command center |
| Right-click a task link → **Edit properties** | Change status, priority, dates |
| Filter by tag | Click a `#tag` in the task list to filter |
| Search tasks | Use Obsidian search (`Ctrl+F`) in task view |

---

## Troubleshooting

**"I don't see the Kanban board"**
- Make sure Bases core plugin is enabled
- Run `06 Scheduling: Create files` from command palette to regenerate `.base` files

**"My custom properties aren't showing up"**
- Reload Obsidian (`Ctrl+R` on Windows)
- Make sure YAML syntax is correct (use `property: value`, not `property:value`)

**"I created a task but it's not in the view"**
- Check that the task has the right tag (`#job-search`, `#art`, or `#habit`)
- Verify the YAML frontmatter is valid (no typos in property names)

---

## Next Steps (This Week)

- [ ] Set up Bases plugin
- [ ] Create 5 job search tasks (one per target company)
- [ ] Create this week's daily application tasks (Mon-Fri)
- [ ] Create Sunday's weekly planning task
- [ ] Create art posting tasks (Sun, Wed, Sat)
- [ ] Take a screenshot of your Kanban board (celebrate setup!)

---

**Your job search runs on momentum. These views keep momentum visible.**

Open `[[Job Search & Life Tracking System]]` for full docs and embedded calendar views.

*Last updated: July 3, 2026*
