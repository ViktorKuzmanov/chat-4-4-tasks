# Q4 — Chat Analysis Project (parts 2–4 of 4)

## Company context
Viktor works at **Q4** (q4.sa), an AI-powered financial research and market-intelligence platform for the
**Saudi stock market (Tadawul)**. Users (financial professionals) ask the chat questions about listed companies,
compare financial performance, and get answers **linked to the source documents** (financial statements,
exchange filings, presentations, earnings-call recordings).

Q4's value: saving research time while keeping analysis **verifiable**. A wrong figure can affect an
investment decision or a client report, so **correctness and citations matter most**.

## People
- **Viktor** — does the work (owner of tasks 3 and 4; Jira tickets assigned to Vladimir until Viktor has an account).
- **Vladimir** — lead/reviewer. Requests the export, provides the private folder, labels 30 questions (agreement check),
  picks/approves the random sample, rechecks 20 verdicts, reviews findings. Send suspected data errors to him.
- **Filip** — produces the anonymised production export and flags Q4 team/test accounts.

## The three tasks
- **Part 2 – Statistics**: what clients ask, what data they need, in what form. → `02_statistics/`
- **Part 3 – Correctness**: hand-check 200 random real answers against the original filings. → `03_correctness/`
- **Part 4 – Root causes**: why answers fail, ranked fixes, Jira tickets, 10-min team presentation. → `04_root_causes/`
- Each folder has a `TASK.md` with the full original task description — check it for "done when" and rules.
- Full plan and status: `PLAN.md`. Each part's output feeds the next (2 → 3 → 4).

## Privacy rules (non-negotiable)
- The export contains **real client questions**. It lives ONLY in `data/private/` (or the private folder Vladimir gives).
  `data/private/` is never committed, shared, or uploaded anywhere.
- **Do not paste export content into outside AI tools or websites.** Exception: Vladimir has confirmed (2026-11-17)
  that Claude Code may read the export and use the Q4 web app for this work. Nothing else (no web search, no other tools)
  ever receives export content.
- Anything for Jira / group channels: **counts, percentages, and reworded examples only** — no client names, emails,
  account details, or anything identifying the person asking.
- Don't change any data in Q4. Read-only.
- Never use the dev database for this — it only has test chats.

## Working conventions
- Scripts in `scripts/` (Python). Random sampling is always done by a script with a fixed, recorded seed — never hand-picked.
- Every reported number states its **n** (how many questions/answers it is based on).
- Every percentage comes with its count.
- Label definitions are frozen in `02_statistics/label_definitions.md` before labelling starts; changes are versioned there.
- Deliverables in `deliverables/` (spreadsheets + Jira comment drafts).
- Claude must not enter Q4 passwords. To use the web app, Viktor signs in directly in the browser pane.
