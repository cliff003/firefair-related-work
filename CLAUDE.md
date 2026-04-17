# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

Track related-work scouting for the **FireFair** paper on a **daily** cadence. Target venue: ACM GoodIT 2026. Submission deadline: **2026-05-17**.

FireFair is a three-agent LLM framework for equity-audited wildfire ignition prediction:
- **(A) ML wildfire ignition prediction** — InceptionTime + CutMix ensemble on California meteorological time series.
- **(B) LLM agents + VLM for remote sensing / hazard** — Sentinel-2 Vision-Language Agent, Equity Agent, Report Agent.
- **(C) Environmental justice / spatial fairness** — CDC/ATSDR SVI quartiles, equal-opportunity gap DeltaEO, per-capita alert exposure ratio rho.

**Line C is the weakest-covered line in the current bibliography and the most likely target of reviewer pushback.** Bias daily-sweep effort accordingly.

## Operating rules (durable)

- **Git:** any Claude session working in this repo may `git add <explicit paths>`, `git commit`, and `git push origin main` as part of its normal finishing flow. The initial sweep is done; routine updates can be committed without asking.
- Never force-push, never `--amend`, never `--no-verify`, never `git add -A` / `git add .` (use explicit paths). Never create branches or PRs — push straight to main.
- `firefair_existing.bib` is **read-only**. Use only for dedup.
- `candidates.bib` is **append-only**. Never reorder, delete, or rewrite existing entries; only add new ones at the end of the relevant section.
- `related_work/_INIT_REPORT.md` is the **frozen initial sweep** (2026-04-17). Do not overwrite or replace; reference it when needed and write new deltas to daily files instead.
- `related_work/_INBOX.md` is the running CITE-NOW / DISCUSS list. You may append new entries under a dated sub-heading, but do not remove existing items without user confirmation.
- If a search line produces noisy or off-topic results, **stop** and tell the user what's wrong. Do not push through with a bad filter.

## Files and conventions

- `firefair_existing.bib` — baseline bibliography (13 entries as of initial sweep).
- `candidates.bib` — append-only file for new papers. Structured by section headers:
  - `% Draft-promoted entries` (3 entries the draft cites but weren't in baseline: Dennin, Ji, Modaresi Rad).
  - `% --- Line A additions ---`, `% --- Line B additions ---`, `% --- Line C additions ---`.
- `related_work/_INIT_REPORT.md` — the initial 2026-04-17 comprehensive sweep. 44 kept entries; full counts + consolidated coverage gaps.
- `related_work/_INBOX.md` — living CITE-NOW + DISCUSS list. Read this first to understand what's already flagged.
- `related_work/YYYY-MM-DD.md` — one file per daily run. Write only if there's a delta; otherwise just append a one-line "no new findings" entry to the most recent dated file or skip.

## Lookback windows (different per line)

- **Line A:** past 12 months
- **Line B:** past 18 months
- **Line C:** past 36 months (widest — this is where the bibliography most needs coverage)

For a daily routine, the effective window is narrower: focus on arXiv listings and venue pages posted **since the previous dated report in `related_work/`**. Check that file's date first.

## Daily routine workflow

1. **Dedup setup.** Read `firefair_existing.bib`, `candidates.bib`, and the most recent `related_work/*.md` to know what is already tracked. Do not re-flag anything already in either bib file.
2. **Targeted queries.** Run 1–2 queries per line (see Query seeds below). For a daily cadence, prefer arxiv `list/cs.LG/YYYY-MM` or venue accepted-papers pages filtered by date, rather than broad topical queries.
3. **Fetch abstracts** for promising hits to extract full author list, arxiv ID, submission date, and venue.
4. **Classify** each kept paper with a relevance tag, one-sentence takeaway, one-line relation to FireFair, Action tag, and target section if CITE-NOW.
5. **Append to `candidates.bib`** under the correct line section, preserving existing entries.
6. **Write `related_work/YYYY-MM-DD.md`** (today's date) with:
   - Count of new entries by Action and Line.
   - Details of any new CITE-NOW or DISCUSS items (BibTeX key, target section, one-line why).
   - POST-SUBMIT / WATCH items as a simple list.
   - Any new coverage gaps or competitor-cluster signals.
7. **If new CITE-NOW or DISCUSS items appeared**, also append them to `_INBOX.md` under a dated sub-heading.

If the daily run finds nothing, write a short `related_work/YYYY-MM-DD.md` noting "no new findings" plus the queries that were run. Do not fabricate entries to fill the file.

## Query seeds (starting points)

**Line A:** "wildfire ignition prediction deep learning", "fire risk forecasting neural network California", "burned area prediction ML", "fire spread transformer", "time series classification InceptionTime", "CutMix time series augmentation"

**Line B:** "vision language model remote sensing", "VLM earth observation", "Sentinel-2 foundation model", "LLM agent disaster", "multi-agent hazard prediction", "agentic AI environmental", "WildfireGPT"

**Line C:** "algorithmic fairness spatial prediction", "equal opportunity geographic ML", "social vulnerability machine learning wildfire", "environmental justice AI", "CalEnviroScreen fairness", "wildfire smoke exposure disparity", "flood risk fairness", "equity audit spatial model"

## Author clusters to monitor

These groups have produced multiple on-topic 2025 papers; scan their latest output each week:

- **Papoutsis / Camps-Valls / Kondylatos / Prapas / Michail (Athens cluster)** — FireCastNet, TeleViT, SeasFire cube, Uncertainty-Aware wildfire danger, Mediterranean spread forecasting. Dominant Line A lab lineage.
- **Cheng group (ENPC Paris): Sibo Cheng, Zhengsen Xu, Jiahe Zheng, Yihang Zhou** — spread prediction, dynamic firebreaks, CA remote-sensing case studies.
- **Argonne / U Penn: Yangxinyu Xie, Tanwi Mallick, Camillo Taylor** — WildfireGPT → MARSHA (npj Climate Action 2025). Line B.
- **FireCastRL / Vereshchaka (SUNY Buffalo)** — RL + helitack. Line A (already cited via `mathur2025firecastrl`).
- **Fairness-for-Earth cluster: Cai & Balestriero (Brown), Saxena & Shahabi (USC)** — FAIR-Earth, Spatial Fairness position paper. Line C method-adjacent.
- **Benmarhnia / Casey / Schwarz (wildfire epidemiology)** — PNAS 2025 subpopulation heterogeneity, Environment International 2025 GRF vulnerability. Line C descriptive epi.

## Tagging conventions

Every new `candidates.bib` entry should have a comment line above it with:

```
% [relevance-tag][relevance-tag-2] ACTION -- brief target / rationale
```

**Relevance tags** (one or more):
- `[A-predict]` — ML wildfire prediction
- `[B-agent-vlm]` — LLM agents / VLM for remote sensing / hazard
- `[C-equity]` — EJ / spatial fairness
- `[baseline]` — a method our paper could reasonably compare to
- `[dataset]` — a dataset or benchmark
- `[method]` — a metric / auditing technique

**Action tags:**
- `CITE-NOW` — reserved for (a) direct competitors not yet cited, (b) methods a reviewer will ask "why didn't you compare to", or (c) fairness work that directly challenges DeltaEO / rho. Always specify target section. Bias *against* this tag — every CITE-NOW is a revision cost.
- `DISCUSS` — affects framing, needs user judgment. Give 2–3 sentence rationale and commit to a recommendation.
- `POST-SUBMIT` — relevant but not worth the revision cost before 2026-05-17.
- `WATCH` — not actionable now; track in case the deadline slips.

## BibTeX style guide

Match the style already in `firefair_existing.bib`:

- Citation keys: `firstauthorlastname` + year + short slug, e.g., `michail2026firecastnet`, `bhowmik2025cawfi`, `huynh2024mitigating`.
- Prefer `@article` / `@inproceedings` / `@book` over `@misc` when a peer-reviewed venue is confirmed. Use `@misc` with `eprint` + `archivePrefix = {arXiv}` + `primaryClass` for arXiv preprints.
- If a field (arXiv ID, DOI, volume, author list) isn't verifiable from the search result, write `% TODO: verify` in the `note` rather than guessing.
- Preserve placeholder `note` fields like `Fill in DOI from Zotero` — these are deliberate TODOs for the user, not errors to silently "fix."
- For web sources, include `Accessed YYYY-MM-DD` in `note`.
- When user-supplied year conflicts with canonical publication year, keep canonical and add a `%` comment (see `abatzoglou2013gridmet` in the baseline bib).

## Keep / drop filter

**Keep** if at least one of:
- Direct overlap with Line A / B / C (strong cite candidate).
- A baseline or ablation FireFair could reasonably use.
- A fairness-metric critique or extension relevant to DeltaEO / rho.
- A relevant dataset or benchmark.

**Drop:**
- Generic fire physics without ML.
- Unrelated time-series theory.
- General LLM alignment work without hazard grounding.

## Known competitors and coverage gaps (from initial sweep)

Pre-existing signals the daily agent should keep in context; do not duplicate-flag these:

- **`markov2025firescope` (arXiv:2511.17171)** is the closest peer to FireFair's Sentinel-2 VLA. Sentinel-2 + climate + expert risk rasters + chain-of-thought. Any new paper combining these inputs should be flagged immediately.
- **`xie2025marsha` (npj Climate Action 4:70, 2025)** replaces the existing `xie2025wildfiregpt` cite. Same lead author, peer-reviewed evolution. If a newer MARSHA-2 or WildfireGPT-3 appears, flag as CITE-NOW.
- **`bhowmik2025cawfi` (arXiv:2509.11015)** is the only 2025 CA-wide ignition-adjacent dataset. New CA datasets are high-priority finds.
- **No 2025 paper applies CutMix to wildfire time series.** If one appears, flag immediately — it would be an external validation of FireFair's augmentation contribution.
- **No wildfire-prediction ML model in the sweep audits itself with equal-opportunity or per-capita disparate-exposure.** FireFair is (as of the 2026-04-17 sweep) first. Any new paper that audits a hazard-prediction model with DeltaEO / rho / disparate-impact style metrics is a **CITE-NOW in Line C** and a material change to FireFair's framing.
- **No VLM-for-wildfire paper computes any fairness / EJ metric.** Any new one would be a CITE-NOW for Line B and would collapse FireFair's current "Equity Agent stands alone" framing.
- **ICLR 2026 was still under review at the time of the initial sweep** (conference 2026-04-23 to 04-27). Rerun Line A and Line B search on the OpenReview ICLR-2026 accepted-papers page once it opens.

## Deadline-aware triage

We are within ~30 days of the 2026-05-17 submission. **Bias hard toward POST-SUBMIT and WATCH.** Every new CITE-NOW has a non-zero narrative cost. A paper must clear one of these three bars to be CITE-NOW:

1. It is a direct competitor and would be a visible omission in Related Work.
2. A reviewer will ask "why didn't you compare to this?"
3. It directly challenges DeltaEO / rho or the Equity Agent's correctness.

Anything else is POST-SUBMIT or WATCH.
