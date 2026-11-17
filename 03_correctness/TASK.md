# Chat analysis 3 of 4 — Measure how many answers to real client questions are correct

> Original task description, organized for reference.
> Previous: part 2 → `../02_statistics/TASK.md` · Next: part 4 → `../04_root_causes/TASK.md`

**For:** Viktor. Assigned to Vladimir until Viktor has a Jira account.
**Input:** the export and labels from **part 2**.

---

## 1. Goal
- Get a **real correct rate** for the answers clients received.
- Our existing benchmark of about **300 questions** uses questions we wrote ourselves, so it doesn't show this.
- The code has **no thumbs up or down** on chat answers, so answers have to be **checked by hand**.

---

## 2. Sample
- **Vladimir or a script** picks **200 random answers**. Don't choose them yourself, or the sample will drift toward easy ones.
- Include **at least 30 Arabic answers**, and **at least 15 of each common question type** from part 2.
- If a group is topped up this way, **state it**, and **weight the overall figure back to the real mix**.
- With 200 answers, the overall figure is accurate to about **± 7 percentage points**. Small groups are much less exact, so **show their counts too**.

---

## 3. How to check each answer
Check it against the **original filing**, **not** against Q4's own stored data:

1. **Did it answer what was asked?**
2. **Is each number right**, including company, period, unit and scale (million vs billion, three months vs year to date)?
3. **Does each citation open a source that really supports the sentence?**
4. **Is any statement not in the sources**, such as an invented reason?

---

## 4. Verdict for each answer
| Verdict | Meaning |
|---|---|
| **Correct** | Everything checks out. |
| **Partly correct** | The main answer is right, but something is missing or a detail is wrong. |
| **Wrong** | The main answer or a key number is wrong. |
| **No answer** | It refused, failed or said the data wasn't there. **Note whether the data really was missing.** |
| **Can't verify** | Say why. |

**Extra flag — Dangerous:** mark it if the answer **states a wrong number confidently**, because that is the failure that loses a client's trust.

---

## 5. Results to report
- **Overall percentage for each verdict**, plus the **dangerous rate**
- The same split by:
  - question type
  - language
  - model
  - month (older answers came from older versions of the chat)
- Whether **citations were right**, as a separate percentage

---

## 6. Quality check
- **Vladimir rechecks 20** of your answers **without seeing your verdicts**.
- If you disagree on **more than 3**, agree the rules and **recheck the affected group**.

---

## 7. Done when
- [ ] A **spreadsheet** holds each answer, its verdict, what was wrong and the source page used.
- [ ] A **comment here** (Jira) gives the **results table** and **5 reworded examples of serious errors**.

---

## 8. Rules
- The **same privacy rules as part 2** apply.
- **Don't change any data.**
- Send **suspected data errors to Vladimir**.

---

## Files in this folder
| File | Purpose |
|---|---|
| `TASK.md` | This description |
| `verdict_rules.md` | Detailed checking rules / edge cases |
| `sample_log.md` | Seed, sample size, top-ups, weights |
| `vladimir_recheck.md` | 20-answer blind recheck and disagreements |
| `data_errors_log.md` | Suspected Q4 data errors sent to Vladimir |
| Output → `../deliverables/part3_verdicts.xlsx` | Each answer + verdict + what was wrong + source page |
| Output → `../deliverables/jira_comments/part3_results.md` | Results table + 5 reworded serious errors |
