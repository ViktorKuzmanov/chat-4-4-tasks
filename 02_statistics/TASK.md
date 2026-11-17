# Chat analysis 2 of 4 — Full statistics on what clients ask, which data they need and in what form

> Original task description, organized for reference. Next: part 3 → `../03_correctness/TASK.md`

---

## 1. Getting the data
- Real questions exist only on the **live site**. The dev database holds test chats, so it can't be used here.
- **Vladimir** asks **Filip** for an anonymised export of chat questions and answers, with client names, emails and account details removed.
- Each row needs:
  - anonymous user number
  - date
  - question
  - answer
  - model
  - citations

  (Each chat's turns hold these fields.)
- **Filip** marks the Q4 team and test accounts so they can be left out.

---

## 2. Statistics to produce
**Give a count and a percentage for each item.**

### 2.1 Usage
- Period covered, total questions, total chats and active users
- Questions per user and per week
- How concentrated usage is: the share of questions from the **top 5 users**
- How many questions and accounts were left out as internal

### 2.2 Question type (one main label per question)
| # | Label |
|---|---|
| 1 | Single figure |
| 2 | Full statement |
| 3 | Comparison |
| 4 | Calculation |
| 5 | Chart |
| 6 | Share price |
| 7 | News |
| 8 | Earnings call |
| 9 | Reading a document |
| 10 | Screening across companies |
| 11 | Macro or government data |
| 12 | Follow-up |
| 13 | Other |

### 2.3 Data needed
| # | Label |
|---|---|
| 1 | Financial statements |
| 2 | Notes |
| 3 | Board reports |
| 4 | Earnings calls |
| 5 | Announcements |
| 6 | Prices |
| 7 | Dividends |
| 8 | Government data |
| 9 | Data Q4 doesn't have |

### 2.4 Companies
- Most asked companies (**top 20**) and sectors

### 2.5 Period asked about
- Latest quarter
- Latest year
- Several years
- None stated

### 2.6 Form they want it in
- One number
- Table
- Chart
- Written summary
- Exact quote
- Excel
- List of companies

### 2.7 Language
- English
- Arabic
- Mixed

---

## 3. Method
- Label **every** question if there are **1,000 or fewer**.
- If there are more, label a **random 500 chosen by a script**, and **state that in the results**.
- Write the **label definitions down first**, with **one example each**.
- Have **Vladimir label 30 of the same questions** separately. Report how often you both agree, and **tighten the definitions if you agree on fewer than 80%**.

---

## 4. Done when
- [ ] A **spreadsheet** holds every labelled question.
- [ ] A **comment here** (Jira) gives a **one-page summary** with the tables above and the **5 clearest findings**.
- [ ] The summary says **how many questions it is based on**, so nobody over-reads a small sample.

---

## 5. Rules
- These are **real clients' questions**.
- Keep the export in the **private folder Vladimir gives you**.
- Don't share it in group channels, and don't paste it into outside AI tools or websites.
  *(Exception confirmed by Vladimir: Claude Code may read the export for this work.)*
- Anything posted in Jira must be **counts or reworded examples** with **no client or company-identifying details about the person asking**.

---

## Files in this folder
| File | Purpose |
|---|---|
| `TASK.md` | This description |
| `label_definitions.md` | Label definitions + one example each (to write first) |
| `agreement_check.md` | Viktor vs Vladimir on 30 questions |
| Output → `../deliverables/part2_labelled_questions.xlsx` | All labelled questions |
| Output → `../deliverables/jira_comments/part2_summary.md` | One-page Jira summary |
