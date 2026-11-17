# Chat analysis 4 of 4 — Find the main reasons answers go wrong and where to improve first

> Original task description, organized for reference.
> Previous: part 3 → `../03_correctness/TASK.md`

**For:** Viktor. Assigned to Vladimir until Viktor has a Jira account.
**Input:** the **verdicts from part 3** and the **statistics from part 2**.

---

## 1. Goal
Explain **why answers fail** and **rank what to fix first**, based on how often each problem hits real clients.

---

## 2. Steps

### Step 1 — Collect failures
Take every answer marked **wrong, partly correct, no answer or dangerous** in part 3.

### Step 2 — Give each one main reason
| # | Reason | Meaning |
|---|---|---|
| 1 | **Data missing** | Q4 doesn't hold the filing, figure or period. |
| 2 | **Data wrong** | Q4 stored the wrong value, such as a misread digit or wrong scale. |
| 3 | **Wrong source chosen** | The right data exists, but the chat used another document or period. |
| 4 | **Misread or miscalculated** | The source was right, but the answer states or calculates it wrongly. |
| 5 | **Not in the sources** | The answer added a claim or reason the source doesn't give. |
| 6 | **Citation wrong** | The answer is right, but the link is missing or goes to the wrong place. |
| 7 | **Failed or too slow** | An error or timeout. |
| 8 | **Not supported** | The product can't do this yet. |
| 9 | **Unclear question** | The chat should have asked or stated what it assumed. |

**To tell these apart:** first check whether the right figure exists in Q4 on the **company's page**.
Ask **Vladimir or Filip** to help with the cases you can't separate.

### Step 3 — Re-test today
Ask each failed question **again on the current q4.sa**, and note whether it is **now fixed**. Recent fixes may already cover some of them.

### Step 4 — Link to Jira
Search Jira for an existing ticket on each reason, e.g.:
- **DD-169** — missing new filings
- **DD-172** — wrong report being chosen

Note the ticket, or **propose a new one**.

---

## 3. Results to report

### 3.1 Ranked table
| Reason | Failed answers | % of failures | Dangerous | Still failing today | Most affected question type | Jira ticket |
|---|---|---|---|---|---|---|

### 3.2 Top 5 improvements
Ranked by **how many client questions each would fix**, using the **question mix from part 2**. For each:
- The problem in **one sentence**
- **How many answers** it affects
- **Two reworded examples**
- A **suggested fix**

### 3.3 Gaps
List what clients **ask often** that Q4 **can't do or doesn't hold yet**.

---

## 4. Done when
- [ ] A **comment here** (Jira) holds the table and the top 5, **with evidence for each claim**.
- [ ] **Vladimir has reviewed it** and the **agreed items are in Jira**.
- [ ] You have **presented the findings to the team in 10 minutes**.

---

## 5. Rules
- The **same privacy rules as part 2** apply.
- **Reword every example**, and leave out anything that identifies the client.

---

## Files in this folder
| File | Purpose |
|---|---|
| `TASK.md` | This description |
| `reason_rules.md` | How to decide between the 9 reasons (edge cases) |
| `retest_log.md` | Re-asked on current q4.sa → fixed / still failing |
| `jira_mapping.md` | Reason → existing ticket or proposed new one |
| Output → `../deliverables/part4_root_causes.xlsx` | Each failure + reason + retest + ticket |
| Output → `../deliverables/jira_comments/part4_findings.md` | Ranked table + top 5 + gaps |
| Output → `../deliverables/part4_presentation` | 10-minute team presentation |
