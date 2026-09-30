# CFO Agent

The household CFO agent from my second brain — a set of Markdown skill files that run a shared
budget for two people: transaction ingest, weekly pace check-ins, a monthly money date, a
subscription/leak audit, iMessage affordability Q&A, a quarterly zoom-out, and bill → calendar sync.

Every skill is a plain Markdown prompt file. The arithmetic lives in small Python scripts
(`ingest.py`, `categorize.py`, `weekly_report.py`, `affordability.py`, `subscription_scan.py`,
`render_dashboard.py`) that only parse and total — never make judgment calls. All state is Markdown
and CSV, human-readable and human-editable.

## Skills

| File | What it does |
|---|---|
| `skills/transaction-ingest.md` | Normalize bank/Venmo/Mercury CSVs into one ledger, bucket each row, flag what needs review |
| `skills/weekly-money-check-in.md` | Sunday pace / overspend / anomaly check + next-14-day bill calendar |
| `skills/monthly-budget-session.md` | Live "money date" interview: income, bucket discovery, $ allocation, dashboard regen |
| `skills/subscription-audit.md` | New recurring charges, price creep, and the leak flag (cancelled but still charging) |
| `skills/cfo-text-reply.md` | Answer "can I afford X?" over iMessage in 1-3 sentences, never inventing a number |
| `skills/quarterly-review.md` | 3-month bucket trends, self-employment tax set-aside, goals progress |
| `skills/bill-calendar-sync.md` | Push fixed bill due dates to Google Calendar, without duplicates |

## Design rules the skills share

- **Never invent a number.** A figure comes from a script's output or a person's stated answer, or
  the skill says it doesn't have it.
- **Statements, not guesses.** Unparseable rows go to `needs_review.md`, unmatched merchants go to
  `NEEDS-BUCKETS.md` for a human decision, instead of being silently bucketed.
- **Ask before outward action.** Cancelling a subscription or writing to a shared calendar is
  confirmed with the humans first.
- **Markdown is the interface.** Reports are written as notes the household actually reads, not
  buried in logs.

## Layout these skills expect

```
context/finances.md                      household scope + rules
projects/household-money/                BUCKETS, RULES, GOALS, CONTACTS, budgets/YYYY-MM.md
scripts/finance/*.py                     parse + arithmetic (kept out of this repo)
data/finances/transactions.csv           the ledger
logs/finance-checkins/                   weekly + quarterly reports
```

*Personal details in these files (names, business names, local paths) were left as written in my
private second brain; this repo is private for that reason.*
