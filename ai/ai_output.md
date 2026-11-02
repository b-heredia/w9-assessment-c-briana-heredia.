# Task 1 — AI Output

- **Name:**
- **AI tool and model:** (e.g., Gemini 2.5 Flash, ChatGPT GPT-5, Copilot)
- **Date and time prompted:**
- **Data provenance:** (copy the provenance note from `baseline_summary.md`)
- **Columns I removed before prompting (privacy):**

## Prompt I used (copy it exactly)

```text
at 12:10pm I started working on the AI project. Use AI to produce a summary of the dataset. Compare the AI output to the baseline using at least two criteria (e.g., accuracy, completeness, bias, reliability). Decide: accept / edit / reject, and explain why
```

## AI output (copy it exactly; do not fix anything here)

**Project log:** started 12:10 PM CT, Mon Nov 2, 2026 · Dataset: workshop.csv (24 workshops, Mar 3 – May 26, 2026)

## 1. AI-generated summary

> Over 24 digital-skills workshops held across six Chicago neighborhoods, 518 people registered and 394 attended, an attendance rate of about 76%. Participants rated the workshops highly, averaging 4.4 out of 5. **Online Job Search** was the strongest topic: it had the highest rating (4.65) and produced 41 of the 93 follow-up signups (44%). **Weekday 10am sessions underperformed**, with only 56% of registrants attending, compared with 80–86% for evening and Saturday slots. **Intro to Spreadsheets** had the lowest ratings (4.13). Logan Square and Rogers Park had the best attendance (84–86%), and Austin and Englewood had the lowest (68–69%). Recommendation: move morning sessions to evenings or Saturdays, and offer more job-search workshops.

## 2. Baseline (calculated directly from the CSV with Python)

| Metric | Baseline value | AI claim | Match? |
|---|---|---|---|
| Workshops / registered / attended | 24 / 518 / 394 | same | ✅ |
| Attendance rate | 76.1% | ~76% | ✅ |
| Mean rating | 4.43 | 4.4 | ✅ |
| Job Search follow-ups | 41 of 93 (44%), rating 4.65 | same | ✅ |
| Weekday 10am attendance | 55.5% (all 6 of the lowest-attended workshops) | 56% | ✅ |
| Saturday / Weekday 6pm attendance | 86% / 80% | 80–86% | ✅ |
| Spreadsheets rating | 4.13 (lowest) | same | ✅ |
| Neighborhood attendance range | Rogers Park 86%, Logan Sq 84%, Austin 68%, Englewood 69% | same | ✅ |

## 3. Comparison against the criteria

**Accuracy: strong.** Every number in the summary matches the baseline.

**Completeness: partial.** The summary leaves out three things:

- **Sample size.** Each neighborhood had only 4 workshops, and each topic only 6. That's too few to support confident rankings.
- **Confounding.** Austin and Englewood each held 2 of their 4 workshops at Weekday 10am. Their low attendance is probably explained by the time slot rather than the neighborhood.
- **Job Search's follow-up signups don't depend on the time slot.** They stay high even at weekday sessions. This is the most actionable finding, and the summary doesn't mention it.

**Bias: some risk.** Calling Austin and Englewood the "lowest" neighborhoods, without the time-slot explanation, could unfairly label communities on the South and West Sides as less engaged. If that framing reached funders, it could shift where future workshops get held.

**Reliability: moderate.** The calculations are correct. However, the recommendation to "move all morning sessions" goes further than the data supports. Daytime slots may serve people the dataset can't see, such as shift workers, seniors, or caregivers. Only three months of data were available, so the claims need hedging.

## 4. Decision: **EDIT**

I wouldn't reject it, because the facts are accurate and the main findings hold up. I also wouldn't accept it as written, because it omits important context and the neighborhood comparison could mislead. Three edits are needed:

1. Add the caveat: *"Small samples (4–6 workshops per group); treat these as patterns, not conclusions."*
2. Replace the neighborhood ranking with: *"Neighborhood differences mostly reflect time slot. Austin and Englewood each held half their sessions at 10am."*
3. Soften the recommendation to: *"Test moving some 10am sessions to evenings or Saturdays, and survey morning registrants before cutting that slot."*

If you need to submit this, I can make it into a doc with the log time, the summary, the comparison table and the decision.
