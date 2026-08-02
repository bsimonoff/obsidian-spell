---
title: GitHub Agent Credentials
created: 2026-08-02
type: reference
---

# GitHub Agent Credentials (Reference Only)

**⚠️ SENSITIVE INFORMATION — Keep confidential**

## Active Token

**Name:** `SpellJobAgent-Test-2026-08`  
**Created:** 2026-08-02  
**Expiration:** Never (no expiration set)  
**Status:** ✅ Active  
**Scopes:** `repo`, `read:user`, `user:email`

**Storage:**
- **Location:** `.env.local` (git-ignored, local only)
- **Environment variable:** `GITHUB_TOKEN_SPELL`
- **Usage:** Agent reads from `$GITHUB_TOKEN_SPELL` at runtime

---

## How Agent Uses It

1. Agent starts (scheduled Monday 8 AM MST)
2. Reads `$GITHUB_TOKEN_SPELL` from environment
3. Clones/pulls repo: `https://github.com/bsimonoff/obsidian-spell.git`
4. Reads duplicate check against existing Pipeline jobs
5. Commits new jobs via git + pushes to main branch
6. All authenticated via the token

---

## If Token Compromised

1. Go to GitHub → Settings → Developer settings → Tokens (classic)
2. Find `SpellJobAgent-Test-2026-08` and delete it
3. Create a new token (follow same process)
4. Update `.env.local` with new token
5. Restart agent

---

## Regeneration (if needed)

Follow the same process as creation:
1. GitHub → Settings → Developer settings → Personal access tokens (classic)
2. Generate new token
3. Name: `SpellJobAgent-Test-[Date]`
4. Scopes: `repo`, `read:user`, `user:email`
5. Expiration: Never
6. Copy token → paste into `.env.local`
7. Update this note with new token name/date

---

**Last updated:** 2026-08-02
