# Mode: offer — Full Evaluation A-G

When the candidate pastes a job offer (text or URL), ALWAYS deliver all 8 blocks:

## Step 0 — Archetype Detection

Classify the offer into one of these archetypes:
- Data Scientist (ML/Modeling)
- Data Scientist (Product/Growth)
- Analytics Engineer
- Applied Scientist
- ML Engineer
- Adjacent (PM, Solutions, etc.)

If hybrid, indicate the 2 closest. This determines:
- Which proof points to prioritize in Block B
- How to rewrite the summary in Block E
- Which STAR stories to prepare in Block F

## Block A — Role Summary

Table with:
- Archetype detected
- Domain (retail/streaming/adtech/GenAI/fintech/consumer tech)
- Function (build/model/analyze/deploy/manage)
- Seniority
- Remote (full/hybrid/onsite)
- Team size (if mentioned)
- TL;DR in 1 sentence

## Block B — CV Match

Read `cv.md`. Create table mapping each JD requirement to exact lines from the CV.

**Adapted to archetype:**
- If DS/ML → prioritize modeling pipelines, feature engineering, production deployment
- If Analytics Engineer → prioritize dbt, SQL, data pipelines, Snowflake/BigQuery
- If Applied Scientist → prioritize research, experimentation, publications
- If ML Engineer → prioritize MLOps, infrastructure, model serving

**Gaps section** with mitigation strategy for each gap:
1. Is it a hard blocker or nice-to-have?
2. Can the candidate demonstrate adjacent experience?
3. Is there a portfolio project that covers this gap?
4. Concrete mitigation plan (cover letter phrase, quick project, etc.)

## Block C — Level and Strategy

1. **Detected level** in JD vs **candidate's natural level for that archetype**
2. **"Sell senior without lying" plan**: specific phrases adapted to archetype, concrete achievements to highlight
3. **"If they downlevel" plan**: accept if comp is fair, negotiate 6-month review, clear promotion criteria

## Block D — Comp and Demand

Use WebSearch for:
- Current salaries for the role (Glassdoor, Levels.fyi, Blind, myvisajobs.com)
- Company compensation reputation
- Role demand trends

Table with data and cited sources. If no data found, say so instead of guessing.

## Block E — Personalization Plan

| # | Section | Current State | Proposed Change | Why |
|---|---------|---------------|-----------------|-----|
| 1 | Summary | ... | ... | ... |

Top 5 CV changes + Top 5 LinkedIn changes to maximize match.

## Block F — Interview Prep

6-10 STAR+R stories mapped to JD requirements (STAR + Reflection):

| # | JD Requirement | STAR+R Story | S | T | A | R | Reflection |
|---|---------------|--------------|---|---|---|---|------------|

The **Reflection** column captures what was learned or what would be done differently.
This signals seniority — junior candidates describe what happened, senior candidates extract lessons.

**Story Bank:** If `interview-prep/story-bank.md` exists, check if any stories are already there.
If not, append new ones. Over time this builds a reusable bank of 5-10 master stories
that can be adapted to any interview question.

**Framed by archetype:**
- DS/ML → emphasize model impact, business outcomes, production scale
- Analytics Engineer → emphasize data pipeline reliability, stakeholder self-service
- Applied Scientist → emphasize research rigor, experimentation design
- ML Engineer → emphasize system design, latency, reliability

Include:
- 1 recommended case study (which project to present and how)
- Red flag questions and how to handle them (e.g. "why are you leaving Epsilon?", "do you have direct reports?")

## Block G — Posting Legitimacy

Analyze the job posting for signals that indicate whether this is a real, active opening.

**Ethical framing:** Present observations, not accusations. Every signal has legitimate explanations.

### Signals to analyze:

**1. Posting Freshness:**
- Date posted or "X days ago"
- Apply button state (active/closed/missing)
- If URL redirected to generic careers page, note it

**2. Description Quality:**
- Does it name specific technologies, frameworks, tools?
- Does it mention team size, reporting structure?
- Are requirements realistic?
- Is salary/compensation mentioned?
- Any internal contradictions?

**3. Company Hiring Signals** (2-3 WebSearch queries):
- Search: `"{company}" layoffs {year}`
- If layoffs found: are they in the same department as this role?
<!-- 
**4. Reposting Detection:**
- Check if company + similar role appeared before with a different URL -->

### Output format:

**Assessment:** One of three tiers:
- **High Confidence** — Multiple signals suggest a real, active opening
- **Proceed with Caution** — Mixed signals worth noting
- **Suspicious** — Multiple ghost job indicators, investigate before investing time

**Signals table:** Each signal with finding and weight (Positive / Neutral / Concerning).

**Context Notes:** Any caveats that explain potentially concerning signals.

### Edge cases:
- Government/academic: 60-90 days posting age is normal
- Evergreen/continuous hire: note as pipeline role, not ghost job
- Staff+/executive roles: legitimately stay open for months
- No date available: default to "Proceed with Caution", never "Suspicious" without evidence
- Active recruiter contact: itself a positive legitimacy signal

## Post-Evaluation

**ALWAYS** after generating blocks A-G:

### 1. Save report .md

Save full evaluation to `reports/{###}-{company-slug}-{YYYY-MM-DD}.md`

- `{###}` = next sequential number (3 digits, zero-padded)
- `{company-slug}` = company name lowercase with hyphens
- `{YYYY-MM-DD}` = current date

**Report format:**

```markdown
# Evaluation: {Company} — {Role}

**Date:** {YYYY-MM-DD}
**Archetype:** {detected}
**Score:** {X/5}
**Sponsorship:** {Confirmed | Likely | Unclear | ❌ Not Available}
**Legitimacy:** {High Confidence | Proceed with Caution | Suspicious}
**PDF:** {path or pending}

---

## A) Role Summary
## B) CV Match
## C) Level and Strategy
## D) Comp and Demand
## E) Personalization Plan
## F) Interview Prep
## G) Posting Legitimacy

---

## ATS Keywords
(15-20 keywords extracted from JD for ATS optimization)
```

### 2. Log in tracker

**ALWAYS** log in `data/applications.md`:
- Next sequential number
- Current date
- Company
- Role
- Score (1-5 average)
- Sponsorship status
- Status: `Evaluated`
- PDF: ❌ or ✅
- Report: relative link to report .md

**Tracker format:**

| # | Date | Company | Role | Score | Sponsorship | Status | PDF | Report |