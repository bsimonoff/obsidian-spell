---
status: open
priority: high
scheduled: YYYY-MM-DD
dueDate: YYYY-MM-DD
timeEntries:
  - startTime: YYYY-MM-DDTHH:MM:SS
    endTime: YYYY-MM-DDTHH:MM:SS
tags:
  - task
  - [category-tag]
category: [category-name]
dateCreated: YYYY-MM-DDTHH:MM:SS.000-06:00
---

# [Time Icon] [Task Name] - [Day], [Date]

**Time:** HH:MMam/pm - HH:MMam/pm  
**Description:** Concise 1-2 sentence description of what this block accomplishes and any relevant vault links (e.g., [[CLAUDE.md]], [[GOALS.md]], [[Application Tracker]]). Why this matters to your goals.  
**Goal:** [Specific, measurable outcome for this block]  
**Track in:** [Relevant tracking file if applicable]

---

## Task Breakdown

### Section 1 (HH:MM - HH:MM)
- [ ] Subtask 1
- [ ] Subtask 2
- [ ] Subtask 3

### Section 2 (HH:MM - HH:MM)
- [ ] Subtask 4
- [ ] Subtask 5

### Break (HH:MM - HH:MM)
- [ ] Rest/refresh

---

## Daily Tracking

**Status:** ⬜ Not started / 🟨 In progress / ✅ Complete

**Energy level:** 🔋🔋🔋 (1-5)  
**Mood:** 😊 Good / 😐 Ok / 😔 Bad

**Notes:**

---

## How to Use timeEntries

1. **Set `scheduled` to the date only:** `2026-07-04`
2. **Add `timeEntries` array with start/end times:**
   ```yaml
   timeEntries:
     - startTime: 2026-07-04T09:00:00
       endTime: 2026-07-04T12:00:00
   ```
3. **Use ISO 8601 datetime format** (YYYY-MM-DDTHH:MM:SS)
4. **One task per time block:** Creates clear calendar separation

## Calendar Display

When you view the calendar in TaskNotes, each time-blocked task will appear at its chronological position:
- 6:00am task appears at top
- 9:00am task below that
- And so on throughout the day

The `timeEntries` property makes tasks render at the correct time on the calendar view.

## Time Block Examples

**Morning (6-9am):** 
```yaml
timeEntries:
  - startTime: 2026-07-04T06:00:00
    endTime: 2026-07-04T09:00:00
```

**Work Block 1 (9am-12pm):**
```yaml
timeEntries:
  - startTime: 2026-07-04T09:00:00
    endTime: 2026-07-04T12:00:00
```

**Work Block 2 (1-5pm):**
```yaml
timeEntries:
  - startTime: 2026-07-04T13:00:00
    endTime: 2026-07-04T17:00:00
```

**Personal Time (5-6pm):**
```yaml
timeEntries:
  - startTime: 2026-07-04T17:00:00
    endTime: 2026-07-04T18:00:00
```

**Evening (6-11pm):**
```yaml
timeEntries:
  - startTime: 2026-07-04T18:00:00
    endTime: 2026-07-04T23:00:00
```

---

**Pro tip:** Use this template to structure each day. The `timeEntries` field makes tasks appear chronologically on the calendar!
