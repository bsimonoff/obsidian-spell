# Job Posting Verification & Pipeline Management Protocol

**Cross-reference**: See [[CLAUDE.md]] → "Job Posting Verification (NON-NEGOTIABLE)" for when to use.
Also see [[03 Projects/Job Application/Pipeline - Ranked by ChemE Fit.md]] for how verified status is tracked.

**Automation**: Monday 8 AM MST, an agent discovers jobs, checks for duplicates, and stages them in `Pipeline/Pending Review/` for your review and sorting.

---

## Why this exists

On July 19, 2026 a research pass surfaced several "strong Tier 1" roles that turned out to have **no entry-level opening actually posted** (Solid Power = Process Engineer II/Senior only; AGC Biologics = Senior only) and one whose posting **didn't list ChemE as an eligible major** (Blue Origin R58494 = mechanical/aerospace only). The lesson: *knowing a company hires for a role type is not evidence that a matching req is open right now.* This protocol prevents that error.

Additionally, **duplicate jobs waste time and clutter the pipeline.** This protocol includes a staging workflow to prevent duplicates before they reach your decision queue.

**Prime rule:** Never present a job as a real opportunity until you've confirmed a live requisition that matches the candidate's **level** and **major**. A drafted cover letter proves nothing about whether the posting exists.

---

## The verification workflow

### Step 1 — Try the direct posting URL (WebFetch)
- Fetch the specific req URL and ask whether it's an active posting, plus title/location/req ID/date.
- **404 / "no longer accepting applications" / expired** → the req is dead or the link rotted. Do NOT list it as live. Search for a current sibling req instead.

### Step 2 — Blank fetch? Cross-reference (EXPECTED, ACCEPTABLE)
Most modern ATS (Workday, Greenhouse, iCIMS, etc.) are JavaScript-rendered and return an **empty page** to a fetcher. This is normal — not a failure. Cross-reference against aggregators that index individual reqs:
- **LinkedIn Jobs** — best for req existence + posting date
- **Glassdoor** — open-position counts + titles
- **Indeed / ZipRecruiter** — broad coverage, "now hiring" dates
- **Niche boards** — SpaceTalent (aerospace), EV.Careers (battery/EV), BioSpace (pharma/biotech), Built In (Colorado/Seattle/Chicago tech)
- A match on **2+ sources** with a recent date + matching title/req ID = confident "live."

### Step 3 — Confirm the LEVEL (most common failure)
Verify the open req is **entry-appropriate**: Engineer I, Associate, Early Career, New Grad, or Level I/II for a strong candidate.
- ❌ Only "Engineer II / III / IV / Senior / Principal" open → **no entry fit right now → Watchlist.**
- Internships-only also = Watchlist (note the intern-to-FT pathway as a fallback).
- **⚠️ CRITICAL: Read the full job description, not just the title.** A role may be titled "Engineer I" but require "3–5 years experience" in the must-haves section. This is a reach, not entry-level. Aggregator summaries often miss these caveats. Always fetch or cross-reference the full JD.

### Step 4 — Confirm the MAJOR fits
If the posting names required/eligible majors:
- ChemE listed → genuine fit.
- ChemE absent (e.g., "ME/IE/AeroE only") → mark as **reach**, not a fit; drop priority. Manufacturing-engineer titles are frequently mechanical-coded.

### Step 5 — Record it
In the job file, add a dated banner at the top and capture specifics:
- `✅ VERIFIED [date] — req [ID] live` + exact title + **direct apply URL**
- `⚠️ VERIFIED [date] — live but [caveat: level/major/salary floor]`
- `❌ VERIFIED [date] — no entry-level req open (only [what's open]) → Watchlist`

---

## Pipeline status tags
Every role in [[03 Projects/Job Application/Pipeline - Ranked by ChemE Fit.md]] gets a 🔎 tag:

| Tag | Meaning | Action |
|-----|---------|--------|
| ✅ | Live req confirmed, level + major fit | Apply now |
| ⚠️ | Live but caveat (level/major/salary/location) | Apply with eyes open |
| ❓ | Not yet verified | **Verify before applying** |
| ❌ | No entry req open now | Move to Watchlist; recheck later |

**Never leave a ❓ in the top tier presented as confirmed.** State the uncertainty plainly.

---

## Seasonality (context for "nothing's open")
- **Cohort / rotational / campus programs** — seasonal. Peak **Sept–Nov** (next-summer starts), second wave Feb–Mar. Quietest **Jul–Aug**.
- **Req-based "Engineer I" roles** — hire **year-round**, whenever a team has budget.
- For an already-graduated candidate wanting to start ASAP: **prioritize req-based roles**; treat cohort programs as bonus lottery tickets (many start too late anyway).

---

## Quick checklist (run every time)
- [ ] Direct URL fetched (or 404 noted)
- [ ] If blank, confirmed on 2+ aggregators (LinkedIn/Glassdoor/Indeed/niche board)
- [ ] Level confirmed entry-appropriate (not II/III/Sr)
- [ ] Major confirmed (ChemE listed, or flagged as reach)
- [ ] Real req ID + exact title + direct apply URL captured
- [ ] Dated verification banner added to job file
- [ ] Pipeline 🔎 tag set

---

## Batch Research & Consolidation (for 3+ opportunities)

**When researching multiple jobs (3+)**, use [[03 Projects/Job Application/Company Research Template.md]] as a standardized format. Then consolidate all findings into a **single master research document** using the template structure:

**Master Research Doc template:**
- **Title:** [X] Verified [Position Type] Opportunities — Research Summary
- **Metadata:** Research date, total count, target cities covered, verification status
- **Format:** Separate sections for each opportunity, using Company Research Template fields:
  - Company info table (name, industry, location, size, stage)
  - Position details table (title, salary, benefits, remote/on-site)
  - Role alignment checklist
  - Key responsibilities (bulleted)
  - Required + preferred qualifications
  - "How you stack up" comparison
  - Application materials checklist
  - Timeline + strategy

**Example:** [[03 Projects/Job Application/9 Verified Entry-Level ChemE Opportunities (Research Summary).md]]

**Benefits:**
- Single reference point (vs. hunting through 9 separate files)
- Easy comparison (salary, salary, fit across opportunities)
- Consolidates verification dates + aggregator sources
- Supports strategic prioritization ("apply these 4 first")
- Reduces redundant research

**When to create a master research doc:**
- After 3+ opportunities verified in a batch search
- When you're deciding which roles to prioritize
- As a handoff to collaborators / for team discussion

**Keep individual job files?** Yes — master doc is a summary/planning tool. Individual files stay detailed and updated with application status.

---

## Pipeline Organization & Sorting (Post-Research Workflow)

**Once opportunities are researched and individual files created, organize them immediately into Pipeline folders:**

### Folder Structure (Updated with Staging)
```
03 Projects/Job Application/Pipeline/
├── Pending Review/   ← 🤖 Agent-discovered jobs (NOT YET REVIEWED)
├── Applied/          ← Roles you've already applied to
├── In Process/       ← Roles still under consideration
└── Scrapped/         ← Roles you've decided against
```

**Rule:** No homeless files in Pipeline root. Every opportunity file goes into one of the four subfolders above.

**Key workflow:**
1. **Agent (Monday 8 AM)** discovers jobs → adds to `Pending Review/` (after duplicate check)
2. **You review** `Pending Review/` files → decide to apply or scrap
3. **You move** files to `Applied/`, `In Process/`, or `Scrapped/` based on your decision
4. `Pending Review/` should be empty by end of week (all jobs reviewed and sorted)

### Automation Workflow: Agent Job Discovery (Monday 8 AM MST)

**What happens automatically:**

**Every Monday at 8:00 AM MST**, an Anthropic agent:
1. **Searches job boards** for entry-level ChemE roles in your target cities (Denver, Seattle, NYC, Chicago) + international opportunities
2. **Verifies each posting** using the workflow below (live req, entry level, ChemE fit)
3. **Checks for duplicates** against existing jobs in Pipeline (Applied, In Process, Scrapped)
4. **Stages new jobs** in `Pipeline/Pending Review/` with verification metadata
5. **Commits to git** (auto-synced locally via git-obsi-sync)

**You receive a summary** of what was added to `Pending Review/` — review and sort by end of week.

---

### Duplicate Detection Workflow (Agent + You)

**Agent's duplicate check (automatic):**

Before adding any job to `Pending Review/`, the agent cross-references:
- **Company + Role title** — exact match is duplicate (skip)
- **Company + Req ID** — exact match is duplicate (skip)
- **Company + Location** — if a nearly identical role is already in Applied/In Process/Scrapped, flag as potential duplicate
- **Apply URL** — if the URL already exists in Pipeline, skip

**Format for duplicates:** If a job is discovered that duplicates an existing one, the agent notes it in git commit message:
```
agent: skip duplicate — [Company] [Role] (req [ID]) already in Pipeline/In Process
```

**Your manual catch (for edge cases):**

If you spot a duplicate in `Pending Review/` that the agent missed:
1. **Delete the duplicate file** from `Pending Review/`
2. **Check the original** — update it if job details changed (salary, location, deadline)
3. **Commit to git** with message:
   ```
   chore: remove duplicate [Company] [Role] — consolidated with existing entry
   ```

---

### Individual Opportunity File Format

Each role gets its own `.md` file with this structure:

**Header (YAML frontmatter):**
```yaml
---
company: [Company Name]
role: [Exact Job Title]
location: [City, State]
salary_range: $[min]-$[max]
status: VERIFIED
---
```

**Body (Application tracking section first):**
```markdown
## Application Status

- [ ] Applied
- [ ] Scrapped

**Title Applied As:** ___________________________

---

# [Company] — [Job Title]

[Rest of opportunity details...]
```

### Sorting Procedure

**Step 1: Create individual files**
- Extract each opportunity from research summaries into separate .md files
- All files start in `Pipeline/In Process/` (default bucket for "undecided")

**Step 2: User review & mark checkboxes**
- Open each file in Obsidian
- Read the opportunity details
- Check **[ ] Applied** if you've submitted an application
- Check **[ ] Scrapped** if you've decided against the role
- Leave both unchecked = stays in In Process
- Fill in "Title Applied As" field if applicable

**Step 3: Auto-organize**
- Read checkbox status from each file
- Move to appropriate folder:
  - **Applied ✅** → `Pipeline/Applied/`
  - **Scrapped ✅** → `Pipeline/Scrapped/`
  - **Both unchecked** → `Pipeline/In Process/` (already there)

### Batch Research Consolidation (Best Practice)

**After splicing opportunities from research summaries into individual files:**
1. Move original research summary files to `Opportunities/` (for archival reference)
2. Create individual opportunity files in Pipeline (per format above)
3. Place ALL individual files in `In Process/` initially
4. User sorts by marking checkboxes
5. Auto-organize into Applied/Scrapped/In Process folders

**Benefits:**
- No homeless files cluttering Pipeline root
- Clear default state for undecided opportunities
- Simple sorting workflow (check a box, run sort)
- Master research doc stays in Opportunities/ for later reference

---
