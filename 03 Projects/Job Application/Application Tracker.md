# Application Tracker

**Real-time count of job applications submitted**

---

## 📊 Overall Stats

```dataview
TABLE WITHOUT ID
"Total Applications" as Metric,
length(rows) as Count
FROM "03 Projects/Jobs"
WHERE contains(file.frontmatter, "")
GROUP BY true
```

### Quick Count
**Applications Submitted:** [Use the count below]

---

## 📋 By Industry

### 🌱 Renewable Energy / Green Hydrogen

| Company | Applied? |
|---------|----------|
| [[NREL - Chemical Engineer (Golden, CO)]] | Check: - [ ] APPLIED |
| [[Siemens Energy - Process Engineer (Hydrogen)]] | Check: - [ ] APPLIED |
| [[Plug Power - Hydrogen Systems Engineer]] | Check: - [ ] APPLIED |
| [[Mitsubishi Heavy Industries - Hydrogen Engineer (Tokyo, Japan)]] | Check: - [ ] APPLIED |

**Count: ___ / 4**

---

### ✈️ Aerospace

| Company | Applied? |
|---------|----------|
| [[Boeing - Process Engineer (Seattle)]] | Check: - [ ] APPLIED |
| [[Lockheed Martin - Process Engineer (Denver)]] | Check: - [ ] APPLIED |
| [[Airbus - Process Engineer (Toulouse, France)]] | Check: - [ ] APPLIED |
| [[Ball Aerospace - Process Engineer (Denver)]] | Check: - [ ] APPLIED |
| [[Blue Origin - Manufacturing Engineer I Early Career (Kent WA + Denver)]] | Check: - [ ] APPLIED |
| [[Sierra Space - Manufacturing Engineer I (Louisville, CO)]] | Check: - [ ] APPLIED |

**Count: ___ / 6**

**Leads to build out (need req lookup):** Regeneron – Process Dev Engineer I (Tarrytown/NYC, stretch) · Northrop Grumman – Entry Level (Aurora/Denver)

---

### 💊 Semiconductors & Pharma

| Company | Applied? |
|---------|----------|
| [[Pfizer - Process Engineer (New York)]] | Check: - [ ] APPLIED |
| [[Pfizer - Process Automation Engineer (Andover, MA - 2nd Shift)]] | Check: - [x] APPLIED |
| [[Intel - Process Engineer (Semiconductors)]] | Check: - [ ] APPLIED |

**Count: 1 / 3**

---

## 📈 Application Progress

```
Goal: 150-200 applications by mid-September (buffer for interviews)
Revised Target: 3-4 applications/day (sustainable, quality-focused)

Progress Today (July 6):
[###_________________________________] 5 / 150+ (3%)

Weekly Target: 15-20 applications/week
```

---

## 📝 Manual Tracker (Update Weekly)

| Week | Starting | New Apps | Total | Status |
|------|----------|----------|-------|--------|
| Week 1 (July 3-10) | 0 | 5 | 5 | ⬜ In Progress |
| Week 2 (July 10-17) | ___ | ___ | ___ | ⬜ Pending |
| Week 3 (July 17-24) | ___ | ___ | ___ | ⬜ Pending |
| Week 4 (July 24-31) | ___ | ___ | ___ | ⬜ Pending |
| Week 5 (Aug 1-8) | ___ | ___ | ___ | ⬜ Pending |
| Week 6 (Aug 8-15) | ___ | ___ | ___ | ⬜ Pending |
| Week 7 (Aug 15-22) | ___ | ___ | ___ | ⬜ Pending |
| Week 8 (Aug 22-29) | ___ | ___ | ___ | ⬜ Pending |
| Week 9 (Sept 1-15) | ___ | ___ | ___ | ⬜ Pending |

---

## 🎯 How to Use This Tracker

**When you apply to a job:**
1. Go to the job research file (e.g., `NREL - Chemical Engineer (Golden, CO).md`)
2. Check the box: `- [x] **APPLIED**` (change `[ ]` to `[x]`)
3. Come back here and update the manual count for this week

**Weekly routine (Sundays):**
1. Count applications sent this week
2. Update the table above with new count
3. Check progress toward 50+ goal

---

## 💡 Notes

- **Dataview** (if installed) will auto-count checked boxes, but manual tracking is more reliable
- **Check boxes on job files** = mark application as submitted
- **Update this tracker** weekly to stay on pace (12-15/week)
- **50+ applications = strong pipeline** for interviews by late August

---

*Last updated: July 19, 2026*

*Target: 50+ applications by September 30, 2026*
