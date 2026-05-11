# Mode: fit — Quick Fit Check

Fast pre-filter for browsing LinkedIn and job boards. Checks your background fit, culture signals, and what would stand out to HR — without the full pipeline. No report saved, no PDF, no tracker update.

Accepts one URL or multiple URLs (produces a side-by-side comparison if multiple).

## Step 0 — Fetch JD(s)

For each URL:
1. Playwright (`browser_navigate` + `browser_snapshot`) — preferred for SPAs (Ashby, Lever, Greenhouse, Workday, LinkedIn)
2. WebFetch — fallback for static pages
3. Ask user to paste the JD — if both methods fail

If the user already pasted JD text (not a URL), use it directly.

## Step 1 — Assess 4 dimensions per JD

Read `cv.md` and `config/profile.yml`.

### 1. Archetype Match

Does this role map to the candidate's core archetype?

- **Strong** — the role is exactly what the candidate has been doing
- **Partial** — adjacent; candidate covers 60-80% of the core ask
- **Weak** — stretch role, significant reskilling required

### 2. Background Fit

Map the top 5 JD requirements to `cv.md`. For each requirement:

- ✅ **Direct match** — exact or very close experience from cv.md
- ⚠️ **Adjacent match** — related but not exact; candidate can bridge it
- ❌ **Hard gap** — clearly missing, not easily bridged

Only flag hard gaps. Nice-to-haves that are missing are not blockers and should not appear here.

### 3. Sponsorship
- if this jd explicitly state that they don't sponsor, score should be 0 and flag this for user; if they explicitly state they sponsor, score 1.
- note that most companies don't state anything for sponsorship, score a 0.5 for these cases.

## Step 2 — Output format

### Single URL

```
## Fit Check: {Company} — {Role}

**Archetype:** {detected} | **Match:** Strong / Partial / Weak
**Fit Score:** {X.X}/5
**Verdict:** ✅ Apply | ⚠️ Apply with caveats | ❌ Skip

---

### Background fit
| JD Requirement | Match | Evidence from your CV |
|----------------|-------|-----------------------|
| {req 1} | ✅/⚠️/❌ | {exact line or project from cv.md} |
| {req 2} | ... | ... |

### Watch out for
- {gap or red flag + how to address it}

---
**Next step:** `/career-ops offer {url}` for full evaluation + tailored CV.
```

### Multiple URLs

Produce the per-URL summary above for each, then close with a comparison table:

```
## Fit Comparison

| # | Company | Role | Archetype Match | Fit Score | Verdict |
|---|---------|------|-----------------|-----------|---------|
| 1 | ... | ... | Strong/Partial/Weak | X.X/5 | ✅/⚠️/❌ |
| 2 | ... | ... | ... | ... | ... |

**Top pick:** {Company} — {one-sentence reason}
**Skip:** {Company} — {one-sentence reason}
```

## Scoring weights

Fit Score is a weighted average across the 3 dimensions:

| Dimension | Weight |
|-----------|--------|
| Background fit | 75% |
| Archetype Match | 20% |
| Sponsorship | 5% |

## Rules

- No reports saved to `reports/`
- No PDF generated
- No tracker updated
- Keep output tight — this is a browse-time decision tool, not a deep analysis
- If Playwright is unavailable, use WebFetch and note: "Fetched via WebFetch — paste JD if content looks incomplete"
- Do NOT run comp research, interview prep, or posting legitimacy checks — those belong in `/career-ops offer`
