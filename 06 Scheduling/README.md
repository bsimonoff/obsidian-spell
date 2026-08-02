# 06 Scheduling — 06 Scheduling Job Search Hub

**Organized command center for your job search, art tracking, and daily habits.**

---

## 📁 Folder Structure

### 📖 **Guides/** — Documentation & Setup
Start here if you're new to 06 Scheduling.

- **⚡ Quick Start Guide.md** — 5-step setup + command cheat sheet
- **Job Search & Life Tracking System.md** — Full documentation with embedded Views
- **Start Here.md** — Official 06 Scheduling introduction (from plugin)
- **Migration Summary.md** — What changed from old 06 Schedule
- **the command palette and run 06 Scheduling Open tasks view.md** — How to open task views

**👉 Read these in order:**
1. Start Here.md (2 min)
2. ⚡ Quick Start Guide.md (5 min)
3. Job Search & Life Tracking System.md (reference)

---

### 📋 **Tasks/** — Active & Scheduled Tasks
Your daily work: applications, art, habits, planning.

- **Daily Schedule - July 4, 2026.md** — Template for daily structure (morning → evening)
- **Weekly Schedule - Week of July 7-13, 2026.md** — Weekly overview with goals & check-ins
- **Submit 5 job applications - July 4.md** — Example job quota task
- **Create speedpaint for Sunday TikTok post.md** — Example art creation task
- **Research Valero Energy...md** — Example company research task

**How to use:**
- Duplicate these tasks to create more (change dates + company names)
- Move completed tasks to status "done" in 06 Scheduling view
- Create daily tasks for upcoming week on Sunday evening

---

### 📝 **Templates/** — Copy These to Create New Tasks
*(Currently empty — templates are embedded in Guides/*)*

**To create a new task:**
1. Open one of the example tasks above
2. Right-click file → Duplicate
3. Rename and update the YAML properties
4. Move to Tasks folder

---

### 📊 **Views/** — Bases Queries & Visualization
These `.base` files power your 06 Scheduling views (Kanban, calendar, lists).

**Custom Views:**
- **job-search-board.base** — Application pipeline (Kanban by status)
- **art-growth.base** — Art posts tracker (creation pipeline)
- **daily-habits.base** — Habit completion dashboard

**Default Views (from 06 Scheduling plugin):**
- **tasks-default.base** — Master task list
- **calendar-default.base** — Full calendar view
- **agenda-default.base** — Timeline/agenda view
- **kanban-default.base** — Generic Kanban board
- **mini-calendar-default.base** — Compact calendar
- **pomodoro-stats.base** — Time tracking stats
- **relationships.base** — Task dependencies

---

## 🎯 Quick Navigation

**I'm new to 06 Scheduling:**
→ Read [[06 Scheduling/Guides/⚡ Quick Start Guide]]

**I want to see my job applications:**
→ Open task view (cmd palette) → "Application Pipeline" tab

**I want to create a new task:**
→ Duplicate a task from [[06 Scheduling/Tasks/]] and customize

**I want to track my week:**
→ Open [[06 Scheduling/Tasks/Weekly Schedule - Week of July 7-13, 2026]]

**I need to plan next week:**
→ Every Sunday, use the weekly review checklist

---

## 📅 Typical Workflow

### Morning (6am)
- [ ] Gym + breakfast
- [ ] Review [[06 Scheduling/Tasks/Daily Schedule - July 4, 2026]] (or your specific date)

### Work (9am-5pm)
- [ ] Open 06 Scheduling view: `06 Scheduling: Open tasks view`
- [ ] Start today's job application task
- [ ] Check tasks off as you complete them

### Evening (5pm-11pm)
- [ ] Personal time (protected, non-negotiable)
- [ ] Art creation (if scheduled)
- [ ] Update task statuses ("in-progress" → "done")
- [ ] Log notes in daily task

### Sunday Evening (7pm-7:30pm)
- [ ] Open [[06 Scheduling/Tasks/Weekly Schedule - Week of July 7-13, 2026]]
- [ ] Complete the "Sunday Review" section
- [ ] Create next week's daily tasks (duplicate + customize)

---

## 🔄 Keeping This Organized

**Weekly cleanup (Sundays):**
- Move completed tasks to status "done"
- Archive tasks older than 2 weeks (set status to "done")
- Delete example tasks if they pile up

**Monthly:**
- Review the Guides folder (update if needed)
- Check that all task YAML is valid (no typos in properties)
- Clean up old Views if creating custom ones

**When adding new custom Views:**
- Save to **Views/** folder
- Follow the naming pattern: `purpose-name.base`
- Document in this README

---

## 📞 Need Help?

| Question | Answer |
|----------|--------|
| "How do I create a task?" | Read [[06 Scheduling/Guides/⚡ Quick Start Guide]] — Step 3 |
| "Where do I put new tasks?" | In **Tasks/** folder (or duplicated from examples) |
| "How do I use the Views?" | Open `06 Scheduling: Open tasks view` from command palette |
| "My task didn't show up in a View" | Check: tag is correct (#job-search, #art, #habit) + YAML is valid |
| "Can I create custom Views?" | Yes — duplicate a `.base` file from **Views/** and modify |

---

## ✅ Status

- **Created:** July 3, 2026
- **Last organized:** July 3, 2026
- **System:** 06 Scheduling + Obsidian Bases
- **Total tasks:** 5 examples + unlimited custom

---

**Start with [[06 Scheduling/Guides/⚡ Quick Start Guide]] if you haven't read it yet.** 🚀
