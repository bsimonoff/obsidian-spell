# Job Posting Verification Protocol

**Cross-reference**: See [[CLAUDE.md]] → "Job Posting Verification (NON-NEGOTIABLE)" for when to use.
Also see [[03 Projects/Job Application/Pipeline - Ranked by ChemE Fit.md]] for how verified status is tracked.

---

## Why this exists

On July 19, 2026 a research pass surfaced several "strong Tier 1" roles that turned out to have **no entry-level opening actually posted** (Solid Power = Process Engineer II/Senior only; AGC Biologics = Senior only) and one whose posting **didn't list ChemE as an eligible major** (Blue Origin R58494 = mechanical/aerospace only). The lesson: *knowing a company hires for a role type is not evidence that a matching req is open right now.* This protocol prevents that error.

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
