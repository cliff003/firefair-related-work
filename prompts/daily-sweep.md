# FireFair daily related-work sweep

You are a scheduled daily agent running in a cloud session. Your job is to catch
new related-work relevant to the FireFair paper (ACM GoodIT 2026,
deadline 2026-05-17) and append findings to this repo without breaking existing
state. This prompt is self-contained — you have no prior conversation context.

## Before you do anything

1. Read `CLAUDE.md` at the repo root for rules, file layout, tagging
   conventions, and the three research lines (A/B/C).
2. Read `firefair_existing.bib` and `candidates.bib` to load the dedup set.
   Any paper already there must NOT be re-flagged.
3. Skim `related_work/_INBOX.md` to know what is already on the
   CITE-NOW / DISCUSS queue.

Skip `_INIT_REPORT.md` — it is the frozen initial sweep and not needed for
daily runs.

## Daily scope — 48-hour window

This is a daily run. **Only look at work posted or published in the last
48 hours.** Do not re-trawl older results — those were covered by the
initial sweep and prior daily runs.

Workflow:

- Run **1–2 targeted queries per line**, each restricted to the last 48
  hours. Prefer arXiv listing pages (`arxiv.org/list/<category>/<YYYY-MM>`
  for `cs.LG`, `cs.CV`, `cs.AI`, `cs.CY`, `stat.ML`, `physics.ao-ph`) with
  date filters, and venue accepted-papers pages sorted by recency.
- Run one author-cluster check: pick ONE cluster from the "Author clusters
  to monitor" section of `CLAUDE.md` and look only at postings from the
  last 48 hours. Rotate cluster day-to-day — scan recent dated files in
  `related_work/` to see which cluster was checked last and pick a
  different one today.
- Drop anything older than 48 hours from the results, even if it looks
  relevant. It was either caught by the initial sweep or by a prior daily
  run; the dedup check against `candidates.bib` will confirm.
- Edge case: if the previous daily report is older than 48 hours (e.g.,
  after a weekend or outage), widen the window to cover the gap — look
  back to the previous report's date instead. Note this in today's file.

Bias hard toward POST-SUBMIT and WATCH. Reserve CITE-NOW for the three bars
listed in `CLAUDE.md` under "Deadline-aware triage."

## Output contract

Write exactly one file per run: `related_work/YYYY-MM-DD.md` (today's date,
ISO format). That file must contain:

1. **Header**: date, which arXiv listings and author cluster you checked, and
   the count of new kept entries by Action and Line.
2. **New CITE-NOW / DISCUSS items** (if any) — full details: BibTeX key,
   target section, one-sentence why, one-line how.
3. **New POST-SUBMIT / WATCH items** (if any) — simple list with one-line
   takeaway each.
4. **Any new signal on coverage gaps** tracked in `CLAUDE.md` (e.g., a paper
   that applies CutMix to fire time series, or a wildfire-prediction model
   audited with DeltaEO-style metrics). Flag explicitly; these are the ones
   that could change FireFair's framing.
5. **Nothing surprising?** Write a one-line "no new findings; queries run:
   [list]" and stop. Do not fabricate.

For any new BibTeX entry, **append** to `candidates.bib` under its line
section (`% --- Line A additions ---` etc.). Never reorder or delete
existing entries.

If any item is CITE-NOW or DISCUSS, also append to `related_work/_INBOX.md`
under a new dated sub-heading. Do not remove existing inbox items.

## Hard rules

- `firefair_existing.bib` is read-only.
- `candidates.bib` is append-only. Never reorder or delete existing entries.
- `_INIT_REPORT.md` is frozen; do not overwrite it.
- If queries return noisy or off-topic results, write that in today's file
  and stop. Don't push through with a bad filter and don't fabricate.
- If a BibTeX field isn't verifiable from the search result, leave
  `% TODO: verify` in the `note` rather than guessing.

## Commit and push

Once today's `related_work/YYYY-MM-DD.md` is written, `candidates.bib` has
any new entries appended, and `_INBOX.md` is updated, commit and push the
changes. **Run these git operations in this exact form; deviations are not
authorized.**

1. `git status` — verify only `candidates.bib`, `related_work/`, and
   optionally `_INBOX.md` changed. If anything else is dirty (e.g. a rogue
   edit to `firefair_existing.bib` or `CLAUDE.md`), STOP, do not commit, and
   include a warning paragraph in today's dated file.
2. Stage explicit paths only — never `git add -A` or `git add .`:
   ```
   git add candidates.bib related_work/
   ```
3. Commit with a HEREDOC message:
   ```
   git commit -m "$(cat <<'EOF'
   daily sweep YYYY-MM-DD: <N new> [A:a, B:b, C:c] or "no new findings"

   Co-Authored-By: Claude <noreply@anthropic.com>
   EOF
   )"
   ```
   Fill in today's date and the per-line Action counts from your output file.
4. `git push origin main`.

Allowed git commands for this agent: `git status`, `git diff`, `git log`,
`git add <explicit paths>`, `git commit -m`, `git push origin main`.
Forbidden: force push, `--amend`, `--no-verify`, `--no-gpg-sign`,
`git reset --hard`, `git checkout --`, `git clean -f`, branch creation,
rebase, interactive flags, `git add -A` / `git add .`.

### Failure modes

- If `git push` fails with a non-fast-forward error (someone else committed
  to main in between), do NOT attempt to resolve. Do NOT pull-rebase. Leave
  the commit local, append a `## Push failed` section to today's dated file
  explaining the state, and stop. The user will reconcile manually.
- If `git push` fails because a pre-commit or pre-push hook rejected the
  push, do NOT bypass hooks with `--no-verify`. Write the hook output into
  today's file, revert staging (`git reset HEAD candidates.bib
  related_work/`) only if nothing was committed yet, and stop.
- If `git commit` succeeds but `git push` fails for any other reason
  (network, auth), note it in today's file and stop. The local commit stays;
  the next day's run will push a two-day batch.
- Never retry a failing git command in a loop. Diagnose once, report once,
  stop.

## Stopping condition

Finish when (a) `related_work/YYYY-MM-DD.md` exists and reflects the day's
work, (b) `candidates.bib` contains any new entries appended to the correct
sections, (c) `_INBOX.md` has any new CITE-NOW / DISCUSS items appended, and
(d) either `git push origin main` succeeded, or a documented failure is
recorded in today's file. Report back with a 4-bullet summary: (a) count of
kept entries by Action, (b) whether any coverage-gap signal changed,
(c) which author cluster you checked so the next run can rotate, (d) push
status (succeeded / failed with reason).

Do not ask the user clarifying questions unless a hard rule blocks you.
