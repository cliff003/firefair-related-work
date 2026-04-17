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
4. **List `related_work/` and open the most recent `YYYY-MM-DD.md` file.**
   Parse its YAML frontmatter (see "Output contract" below). You need two
   fields from it:
   - `window_end` — the upper bound of the previous run's lookback. Your
     new lookback starts here.
   - `cluster_checked` — the author cluster the previous run checked. You
     must pick a DIFFERENT one today.

Skip `_INIT_REPORT.md` — it is the frozen initial sweep and not needed for
daily runs.

## Daily scope — lookback window

Let `now` be the current timestamp and `prev_window_end` be the value
parsed from the most recent daily file's frontmatter (or `now - 48h` if no
prior daily file exists).

**Your lookback window is `[window_start, now]` where:**

```
window_start = min(now - 48h, prev_window_end - 6h)
```

The `- 6h` is a safety buffer against arXiv posting-batch timing jitter and
timestamp drift between runs. Intent: always cover at least 48 hours, and
if the previous run ended earlier than 48h ago (late run, outage, weekend),
always cover the gap plus 6h of overlap. Overlap is harmless — the dedup
check against `candidates.bib` removes duplicates.

Record `window_start` and `window_end = now` (both ISO-8601 UTC) in today's
frontmatter.

Workflow:

- Run **1–2 targeted queries per line**, each restricted to
  `[window_start, now]`. Prefer:
  - `https://arxiv.org/list/<archive>/recent` — latest 5 days of submissions
    (most useful for the typical 48h window). Valid archives:
    `cs.LG`, `cs.CV`, `cs.AI`, `cs.CY`, `stat.ML`, `physics.ao-ph`.
  - `https://arxiv.org/list/<archive>/new` — today's submissions only.
  - `https://arxiv.org/list/<archive>/YYMM` — full month (NOT `YYYY-MM`).
    Use only if `window_start` is older than 5 days, which only happens
    after long outages.
  - Venue accepted-papers pages sorted by recency.
- Run one author-cluster check: pick ONE cluster from the "Author clusters
  to monitor" section of `CLAUDE.md` whose name is NOT equal to the
  `cluster_checked` field of the most recent daily file. Look only at
  postings inside your window.
- Drop anything older than `window_start`, even if it looks relevant.
  (Dedup against `candidates.bib` will catch anything already captured.)

Bias hard toward POST-SUBMIT and WATCH. Reserve CITE-NOW for the three bars
listed in `CLAUDE.md` under "Deadline-aware triage."

## Output contract

Write exactly one file per run: `related_work/YYYY-MM-DD.md` (today's date,
ISO format). The file MUST start with a YAML frontmatter block so the next
day's agent can parse it deterministically:

```yaml
---
date: 2026-04-18
window_start: 2026-04-16T10:00:00Z
window_end: 2026-04-18T10:00:00Z
cluster_checked: Cheng group
archives_checked: [cs.LG/recent, cs.CV/recent]
counts:
  A: {cite_now: 0, discuss: 0, post_submit: 1, watch: 0}
  B: {cite_now: 0, discuss: 1, post_submit: 0, watch: 0}
  C: {cite_now: 0, discuss: 0, post_submit: 0, watch: 0}
---
```

All fields are mandatory — the next daily run parses `window_end` and
`cluster_checked` from this block. `cluster_checked` must exactly match one
of the cluster names (verbatim, including capitalization) listed under
"Author clusters to monitor" in `CLAUDE.md`.

After the frontmatter, include the following body sections:

1. **New CITE-NOW / DISCUSS items** (if any) — full details: BibTeX key,
   target section, one-sentence why, one-line how.
2. **New POST-SUBMIT / WATCH items** (if any) — simple list with one-line
   takeaway each.
3. **Any new signal on coverage gaps** tracked in `CLAUDE.md` (e.g., a
   paper that applies CutMix to fire time series, or a wildfire-prediction
   model audited with DeltaEO-style metrics). Flag explicitly; these are
   the ones that could change FireFair's framing.
4. **Nothing found?** Write "no new findings" plus the list of queries you
   ran. Do not fabricate entries. Frontmatter still required (all counts
   zero).

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

Finish when (a) `related_work/YYYY-MM-DD.md` exists with valid YAML
frontmatter and reflects the day's work, (b) `candidates.bib` contains any
new entries appended to the correct sections, (c) `_INBOX.md` has any new
CITE-NOW / DISCUSS items appended, and (d) either `git push origin main`
succeeded, or a documented failure is recorded in today's file. Report
back with a 4-bullet summary: (a) count of kept entries by Action,
(b) whether any coverage-gap signal changed, (c) the cluster you checked
(must match `cluster_checked` in today's frontmatter), (d) push status
(succeeded / failed with reason).

Do not ask the user clarifying questions unless a hard rule blocks you.
