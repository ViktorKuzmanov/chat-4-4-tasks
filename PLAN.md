# Plan — Chat analysis parts 2, 3, 4

Dependency chain: **Part 2 (labels + stats) → Part 3 (verdicts) → Part 4 (root causes)**.
Nothing in part 3 can start until part 2's labels exist; part 4 needs part 3's verdicts.

Legend: [ ] todo · [~] in progress · [x] done · 🔒 blocked on someone else

---

## Phase 0 — Unblock (do first, mostly messages to send)
- [ ] 🔒 Vladimir → Filip: request anonymised **production** export (anon user id, date, question, answer, model, citations; per chat turn).
- [ ] 🔒 Filip: flag Q4 team + test accounts in the export.
- [ ] 🔒 Vladimir: provide the private folder location.
- [x] Vladimir confirmed Claude Code may read the export and use the Q4 web app (2026-11-17).
- [ ] Ask for export format (CSV/JSON?) and whether citations are URLs/doc IDs — so scripts can be written before data arrives.

## Phase 1 — Prep while waiting (no real data needed)
- [ ] `02_statistics/label_definitions.md` — every label with a definition + one invented example:
      question type (13), data needed (9), period (4), form (7), language (3), company/sector.
- [ ] `scripts/load_export.py` — load export, drop internal accounts, count what was dropped.
- [ ] `scripts/sample.py` — seeded random sampling (500 for part 2 if >1,000 questions; 200 for part 3 with top-ups).
- [ ] `scripts/stats.py` — usage stats + label counts/percentages → tables.
- [ ] Spreadsheet templates: labelling sheet (part 2), verification sheet (part 3), root-cause sheet (part 4).
- [ ] Test all scripts on a small **fake** dataset.

## Phase 2 — Part 2: Statistics
1. [ ] Load export, exclude internal → record counts excluded (questions + accounts).
2. [ ] Usage stats: period, total questions/chats, active users, questions per user & per week, top-5-user share.
3. [ ] Decide scope: ≤1,000 → label all; >1,000 → seeded random 500 (state it).
4. [ ] Pick 30 questions for Vladimir; both label independently → agreement %. <80% → tighten definitions, relabel.
5. [ ] Label all in-scope questions (one main label per dimension).
6. [ ] Top 20 companies + sectors (map companies → Tadawul sector).
7. [ ] Deliverables: `deliverables/part2_labelled_questions.xlsx` + `deliverables/jira_comments/part2_summary.md`
       (one page: tables, 5 clearest findings, n stated).

## Phase 3 — Part 3: Correctness
1. [ ] Script picks 200 random answers (seed recorded); top up to ≥30 Arabic and ≥15 per common question type; record top-ups.
2. [ ] For each answer check against the **original filing** (not Q4's stored data):
       answered the question? · numbers (company/period/unit/scale) · citations support sentence? · unsupported claims?
3. [ ] Verdict: Correct / Partly / Wrong / No answer (was data really missing?) / Can't verify (why) + **dangerous** flag.
       Record what was wrong + source page used.
4. [ ] Vladimir blind-rechecks 20. >3 disagreements → align rules, recheck affected group.
5. [ ] Results: overall % per verdict (weighted back to real mix), dangerous rate, citation-correct %;
       split by question type, language, model, month — always with counts. Note ±7pp margin overall.
6. [ ] Deliverables: `deliverables/part3_verdicts.xlsx` + `jira_comments/part3_results.md` (table + 5 reworded serious errors).
7. [ ] Suspected Q4 data errors → send to Vladimir (log in `03_correctness/data_errors_log.md`).

## Phase 4 — Part 4: Root causes
1. [ ] Take every Wrong / Partly / No answer / Dangerous from part 3.
2. [ ] Assign one main reason (9 categories). First check if the right figure exists on the company page in Q4. Unclear ones → Vladimir/Filip.
3. [ ] Re-ask each failed question on current q4.sa → fixed today? (Viktor signs in; reworded/anonymised questions only.)
4. [ ] Search Jira per reason (e.g. DD-169 missing filings, DD-172 wrong report chosen) → link or propose new ticket.
5. [ ] Ranked table: reason · failed answers · % of failures · dangerous · still failing · top question type · Jira.
6. [ ] Top 5 improvements ranked by client questions fixed (weight by part 2 mix): problem, count, 2 reworded examples, fix.
7. [ ] List of frequent asks Q4 can't do / doesn't hold.
8. [ ] Deliverables: `jira_comments/part4_findings.md` → Vladimir review → agreed items into Jira → 10-min team presentation.

---

Task descriptions: `02_statistics/TASK.md` · `03_correctness/TASK.md` · `04_root_causes/TASK.md`

## Open questions
- Export size — determines label-all vs. 500 sample.
- Which "models" appear in the data, and when did chat versions change (for by-month split)?
- Sector mapping source for Tadawul companies.
