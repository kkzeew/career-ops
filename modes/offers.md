# Mode: offers — Multi-Offer Comparison

Scoring matrix across 10 weighted dimensions.
H-1B sponsorship is shown for awareness only.

## Step 0 — Sponsorship Awareness Check

Before scoring, do a quick sponsorship lookup for each company:
- Check JD explicitly
- Flag status per company (Confirmed / Likely / Unclear / ❌ No)
- Do NOT disqualify — candidate makes the final call after reviewing

## Scoring Matrix

| Dimension | Weight | Criteria 1-5 |
|-----------|--------|--------------|
| CV Match | 60% | 5=90%+ match, 1=<40% match |
| Estimated Comp | 5% | 5=top quartile for role, 1=below market |
| Growth Trajectory | 5% | 5=clear path to next level + PERM history, 1=dead end |
| Remote Quality | 5% | 5=full remote async, 1=onsite only |
| Company Reputation | 5% | 5=top employer + known sponsor, 1=red flags |
| Tech Stack | 5% | 5=cutting edge ML/AI/GenAI, 1=legacy stack |
| Speed to Offer | 5% | 5=fast process <4 weeks, 1=6+ months |
| Culture Signals | 10% | 5=data-driven builder culture, 1=bureaucratic |

For each offer: score on each dimension, weighted total score.
Final ranking + recommendation with consideration, do not make up information.

Ask the user for offers if not already in context. Can be text, URLs,
or references to already evaluated offers in the tracker.