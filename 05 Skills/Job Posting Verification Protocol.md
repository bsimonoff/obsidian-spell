# Agent Job Discovery Protocol

**⚠️ THIS DOCUMENT IS FOR AN AUTONOMOUS AGENT TO READ AND ACT UPON**

**Cross-reference**: See [[CLAUDE.md]] → "Job Posting Verification (NON-NEGOTIABLE)" for context.

---

## AGENT CONFIGURATION & SCHEDULE

**This section defines what the agent does and when.**

### Execution Schedule

```
Cron: 0 8 * * 1 (MST)
Translation: Every Monday at 8:00 AM Mountain Standard Time
```

**Important:** If the scheduled time changes, update the cron expression above. The agent reads this to know when to run.

---

### Permanent Cloud Agent Deployment

**Agent deployed via Anthropic RemoteTrigger (Permanent):**

| Field | Value |
|-------|-------|
| **Trigger ID** | `trig_019g22ZfDdDSAdo6gQhhi4KM` |
| **Name** | Spell Job Discovery Agent - Permanent |
| **Schedule** | Monday 8:00 AM MST (cron: `0 8 * * 1`) |
| **Status** | ✅ ENABLED (never expires) |
| **Model** | claude-sonnet-5 |
| **Tools** | Read, Write, Edit, Glob, Grep, WebFetch, Bash |
| **Repository** | https://github.com/bsimonoff/obsidian-spell.git |
| **Deployment Date** | 2026-08-02 |

**How to reference this agent in future sessions:**
- Trigger ID: `trig_019g22ZfDdDSAdo6gQhhi4KM`
- Check status: RemoteTrigger action "get" with trigger_id
- Update: RemoteTrigger action "update" with trigger_id
- Next run: Every Monday 8 AM MST

**What the agent does (autonomously):**
1. Clones repo from GitHub (uses GITHUB_TOKEN_SPELL env var)
2. Reads this protocol file for configuration
3. Searches job boards: LinkedIn, Indeed, Glassdoor, ZipRecruiter, SpaceTalent, EV.Careers, BioSpace, Built In
4. Verifies 10+ roles per search by cross-referencing on 2+ aggregators
5. Checks for duplicates in existing Pipeline
6. Creates .md files for verified, non-duplicate jobs in Auto Research/
7. Commits to git with summary message
8. Pushes to main branch
9. Reports results

**Agent does NOT rely on chat history or previous sessions** — it reads this protocol for all instructions.

---

### GitHub Access

The agent needs a **permanent GitHub personal access token** to:
- Read the repo (pull current job files for duplicate detection)
- Write job files to `03 Projects/Job Application/Pipeline/In Process/Auto Research/`
- Commit and push to the `main` branch

**Token Setup (ALREADY CONFIGURED):**

The GitHub token is stored securely in `.env.local` (git-ignored).

**Agent runtime:**
- Read environment variable: `$GITHUB_TOKEN_SPELL`
- Use for all GitHub operations (clone, pull, commit, push)
- Token has permissions: `repo`, `read:user`, `user:email`

**Token reference:**
- See [[03 Projects/Job Application/GitHub Agent Credentials.md]] for token management
- Do NOT commit `.env.local` to git (it's in .gitignore)
- If token expires or is compromised, rotate per that document

```
GitHub repo: https://github.com/bsimonoff/obsidian-spell.git
Token env var: GITHUB_TOKEN_SPELL (read from .env.local at runtime)
Working branch: main
Token name: SpellJobAgent-Test-2026-08 (never expires)
```

---

### Target Specification

**Industries to prioritize (in order):**
1. Aerospace (Boeing, Lockheed Martin, Airbus, SpaceX, Ball Aerospace, etc.)
2. Renewable Energy (NREL, Ørsted, EDP, Siemens Energy, etc.)
3. Semiconductors (Intel, TSMC, Samsung, Micron, GlobalFoundries, etc.)
4. Pharmaceuticals & Biotech (Regeneron, Vertex, Amgen, Genentech, Moderna, etc.)

**Industries to avoid:**
- Oil & Gas
- Petrochemicals
- Fossil fuel power plants

**Target US Cities:**
- Denver, Colorado
- Seattle, Washington
- New York, New York (NYC metro)
- Chicago, Illinois

**International (if visa sponsored):**
- Germany
- Netherlands
- France
- Switzerland
- Austria
- Belgium
- Japan
- South Korea
- Hong Kong
- China

**Salary floor:** $70,000 USD annually (or equivalent in local currency)

**Education requirement:** BS in Chemical Engineering (or related; ChemE is preferred)

**Experience requirement:** Entry-level only (0–2 years, Engineer I, Associate, New Grad, Graduate Program, Rotational Program)

---

## AGENT WORKFLOW

### Step 1: Search for Jobs

**Sources to search (in order of priority):**
1. **LinkedIn Jobs** (most comprehensive; allows filtering by level/major)
2. **Indeed** (broad US coverage)
3. **Glassdoor** (includes salary estimates + reviews)
4. **ZipRecruiter** (aggregates from multiple sources)
5. **Niche boards:**
   - SpaceTalent (aerospace/defense)
   - EV.Careers (battery/EV)
   - BioSpace (pharma/biotech)
   - Built In (Colorado/Seattle/Chicago startups)

**Search criteria:**
- Keywords: "Chemical Engineer", "Process Engineer", "Manufacturing Engineer", "Development Engineer" (entry-level titles)
- Filters: Entry-level, BS ChemE or related, located in target cities/countries
- Salary: $70k+ (if displayed)
- Post date: Within last 30 days (active postings)
- Remote: Accept hybrid/on-site only (no full-remote unless exceptional fit)

---

### Step 2: Verify Each Posting

**Verification workflow (in order):**

**2a. Fetch the direct posting URL**
- Use WebFetch to retrieve the job posting page
- Look for: job title, company, location, salary, requirements, posting date
- If fetch returns **404 or "job closed"** → **SKIP** (posting is dead)
- If fetch returns **blank page** (JS-rendered ATS) → proceed to Step 2b

**2b. Cross-reference on aggregators**
- If direct URL returned blank, search for the job on **2+ aggregators** (LinkedIn, Indeed, Glassdoor)
- Confirm:
  - Job title + req ID match
  - Posting date is recent (< 30 days ago)
  - Location matches target city
  - ChemE is listed as an eligible major
- **Live confirmation rule:** Match on 2+ aggregators = confident "live posting"

**2c. Confirm entry-level**
- Read the full job description
- Check: Is the role titled "Engineer I", "Associate", "New Grad", "Graduate Program", "Rotational", or similar?
- Check: Do required qualifications say "0 years experience" or "BS + entry-level"?
- ❌ SKIP if: "Engineer II+", "3–5 years required", "Senior", or "Principal" (these are not entry-level)
- ⚠️ FLAG if: Title is "Engineer I" but description says "prefer 2–3 years experience" (mark as reach, but still add)

**2d. Confirm ChemE fit**
- Read the required/preferred majors list
- ✅ INCLUDE if: ChemE, Chemical Engineering, Chemistry, or Materials Science listed
- ⚠️ FLAG as "REACH" if: Only "ME/EE/IE listed, but role sounds chemistry/process relevant
- ❌ SKIP if: "Mechanical/Aerospace only" and no chemistry mention

**2e. Check salary**
- If posted: Record it
- If not posted: Note as "not disclosed"
- ❌ SKIP if: posted salary < $70k AND no mention of signing bonus/equity

---

### Step 3: Duplicate Detection

**Before adding a job, check if it's already in the Pipeline:**

1. **Read all existing job files** in:
   - `03 Projects/Job Application/Pipeline/Applied/`
   - `03 Projects/Job Application/Pipeline/In Process/`
   - `03 Projects/Job Application/Pipeline/In Process/Auto Research/`
   - `03 Projects/Job Application/Pipeline/Scrapped/`

2. **Compare using these fields:**
   - **Company + Job Title** (exact match = duplicate, SKIP)
   - **Company + Req ID** (if both are known, match = duplicate, SKIP)
   - **Apply URL** (if it's identical to an existing file's URL, SKIP)

3. **If no duplicate found:** Proceed to Step 4

4. **If duplicate found:**
   - Log: `[DUPLICATE SKIP] [Company] [Role] (req [ID]) already in Pipeline/[Applied|In Process|Scrapped]`
   - Do NOT create a new file
   - Do NOT commit
   - Move to next job

---

### Step 4: Format & Create the Job File

**File location:** `03 Projects/Job Application/Pipeline/In Process/Auto Research/[Company] - [Job Title].md`

⚠️ **CRITICAL:** Files MUST be created in `Auto Research/` subfolder, NOT `Manual Research/`. Manual Research is user-curated only.

**File content (template):**

```markdown
---
company: [Company Name]
role: [Exact Job Title from Posting]
location: [City, State/Country]
salary_range: $[min]-$[max] OR "Not disclosed"
req_id: [Requisition ID if available]
apply_url: [Direct link to apply or job posting]
discovered_date: [YYYY-MM-DD]
source: [LinkedIn|Indeed|Glassdoor|ZipRecruiter|SpaceTalent|EV.Careers|BioSpace|BuiltIn]
status: VERIFIED
verification_date: [YYYY-MM-DD]
agent_notes: "[Entry-level confirmed | REACH: reason | FLAG: caveat]"
---

## Application Status

- [ ] Applied
- [ ] Scrapped

**Title Applied As:** (leave blank — user fills in after applying)

---

# [Company] — [Job Title]

## Verification Summary

**Status:** ✅ VERIFIED [date]  
**Verification path:** [Which sources confirmed this | Direct URL fetch successful]  
**Entry-level:** ✅ Confirmed (Engineer I | Associate | New Grad | [exact title from posting])  
**ChemE fit:** ✅ Confirmed (ChemE listed as required/preferred major)  
**Salary:** $[min]-$[max] ✅ Meets $70k floor

---

## Position Details

**Company:** [Company Name]  
**Title:** [Exact job title]  
**Location:** [City, State/Country]  
**Position type:** Full-time | Internship | Rotational Program  
**Remote/Hybrid:** On-site | Hybrid | Remote (if applicable)  
**Salary:** $[min]-$[max] or "Not disclosed"  
**Req ID:** [If available]  
**Posting date:** [Date from source]  
**Apply URL:** [Direct link]

---

## About the Role

[Copy 2–3 key bullet points from the job description about main responsibilities]

---

## Requirements

**Required:**
- [Key requirement 1]
- [Key requirement 2]
- [Key requirement 3]

**Preferred:**
- [Preferred qualification 1]
- [Preferred qualification 2]

---

## Fit Assessment

**Why this is a good fit:**
- Entry-level role (Engineer I / new grad focus)
- Chemical Engineering major explicitly listed
- Aligned industry (aerospace / renewables / semiconductor / pharma)
- Located in target city / visa sponsorship available

**Caveats (if any):**
- [If REACH: "Title is Engineer I but prefers X years experience"]
- [If location: "Hybrid, but X% on-site"]
- [If salary: "Below $70k but strong fit otherwise"]

```

**Instructions for filling the template:**
- Use the actual content from the job posting (copy-paste key details)
- Keep descriptions concise (2–3 bullets, not the entire JD)
- Mark entry-level and ChemE fit status clearly
- Include caveats honestly (prefer 2+ yrs? Remote-only? Below salary floor?)

---

### Step 5: Commit to Git

**After creating/updating all job files, commit with a message:**

```
git commit -m "agent: discover [N] new entry-level ChemE jobs

[Company 1] - [Role] (req [ID]) - ✅ live
[Company 2] - [Role] (req [ID]) - ✅ live
[Company 3] - [Role] - ⚠️ live but reach (prefer X years)

Verified via [LinkedIn|Indeed|Glassdoor|aggregator cross-ref]
No duplicates found in existing Pipeline.

Co-Authored-By: Agent <agent@anthropic.com>
"
```

**Commit rules:**
- Only commit if **at least 1 new job** was added
- If **all jobs were duplicates** (0 new jobs), do NOT commit
- Include a summary of how many jobs were discovered/skipped
- Push to `main` branch immediately after commit

---

## USER WORKFLOW (For Obsidian)

**You don't need to run the agent.** It runs automatically every Monday at 8 AM MST. Here's what you do:**

### Weekly Review (Monday–Friday)

1. **Check `Pipeline/In Process/Auto Research/`** for new jobs
2. **Read each job file** (verify company, role, salary, location look good)
3. **Decide for each job:**
   - **Strong fit?** → Leave it in `Auto Research/` (keep for later)
   - **Weak fit/don't want?** → Move to `Pipeline/Scrapped/`
   - **Ready to apply?** → Move to `Pipeline/In Process/` (non-Auto Research)
4. **After applying:** Move job file to `Pipeline/Applied/` and check `[x] Applied`

### File Management

**Auto Research folder:**
- Jobs the agent added
- Review and sort by moving to Scrapped or Applied
- Organize as needed within Auto Research (by industry, location, date, etc.)

**Applied folder:**
- Jobs you've applied to
- Check `[x] Applied` and fill in "Title Applied As"
- Keep for reference

**Scrapped folder:**
- Jobs you decided against
- Check `[x] Scrapped`
- Archive/reference later

---

## Troubleshooting (For Deployer)

**Agent not running at the scheduled time?**
- Verify GitHub token (`GITHUB_TOKEN_SPELL`) is valid and not expired
- Check agent logs for errors
- Verify cron schedule is correct: `0 8 * * 1 (MST)`

**Agent finding duplicates constantly?**
- Duplicate detection is working correctly
- If legitimate duplicates exist (e.g., multiple req IDs for same role), the agent will skip them
- User should clean up old/stale jobs in Pipeline

**Agent not finding enough jobs?**
- Job market may be slow
- Search may need broader keywords
- Consider expanding target cities or industries

---

## Version History

| Date | Change | Author |
|------|--------|--------|
| 2026-08-02 | Initial agent protocol | Claude |

---

**This document is the source of truth for the agent's behavior. Update it to change what the agent does.**
