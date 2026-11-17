# Q4 Chat Analysis (parts 2–4)

Analysis of real client questions and answers on the Q4 platform (AI-powered research for the Saudi stock market): what clients ask, how often the answers are correct, and why they fail.

## Tasks
| Part | Goal | Folder |
|---|---|---|
| 2 | Statistics on what clients ask, which data they need, in what form | [02_statistics/](02_statistics/TASK.md) |
| 3 | Measure how many answers are correct (200 hand-checked answers) | [03_correctness/](03_correctness/TASK.md) |
| 4 | Find main failure reasons and rank what to fix first | [04_root_causes/](04_root_causes/TASK.md) |

Each part feeds the next: 2 → 3 → 4. Full steps and status: [PLAN.md](PLAN.md).

## Layout
```
CLAUDE.md          Context and rules for Claude sessions
PLAN.md            Step-by-step plan with checkboxes
02_statistics/     Part 2 (TASK.md = original description)
03_correctness/    Part 3
04_root_causes/    Part 4
scripts/           Loading, seeded sampling, stats
data/private/      Real export. Never share or commit
deliverables/      Spreadsheets and Jira comment drafts
```

## Privacy
The export holds real client questions. Keep it only in `data/private/`, never post it in group channels or outside AI tools (Claude Code is approved by Vladimir). Jira gets counts and reworded examples only, with nothing identifying the client.
