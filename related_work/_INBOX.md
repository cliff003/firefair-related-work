# FireFair -- Inbox (CITE-NOW + DISCUSS)

- Date: 2026-04-17 (full re-sweep)
- Deadline: 2026-05-17 (30 days)
- Status: **All three lines complete.**

---

## Line A -- CITE-NOW (3)

1. **`bhowmik2025cawfi`** -- arXiv:2509.11015 -- Section 3 Data (+ Section 2 Related Work Line A).
   - *Why:* New 37M-point California wildfire + covariate dataset (2012-2022). Reviewer will ask.
   - *How:* Add one sentence to related-datasets paragraph; flag CAWFI as out-of-window validation option if time allows.

2. **`michail2026firecastnet`** -- Sci Reports 2026 (arXiv:2502.01550) -- Section 2 Related Work Line A.
   - *Why:* Peer-reviewed SOTA seasonal-fire GNN; sits directly beside `digiuseppe2025global` in the "global neural fire forecasting" cluster.
   - *How:* One sentence next to Di Giuseppe; note FireFair's finer time grain (daily ignition) vs. their seasonal target.

3. **`prapas2025televit`** -- arXiv:2512.00089 -- Section 2 Related Work Line A.
   - *Why:* ViT + teleconnection indices for subseasonal-to-seasonal fire; newest direct competitor in the Papoutsis/Camps-Valls lineage.
   - *How:* Group with FireCastNet; emphasize that our scope is CA-local daily ignition, not global S2S patterns.

## Line A -- DISCUSS (2)

1. **`kondylatos2025uncertainty`** -- arXiv:2509.25017. Uncertainty-aware DL for wildfire danger (+2.3% F1, -2.1% ECE).
   - **Recommendation:** CITE-NOW in Limitations only, one sentence. We don't report UQ; pre-empting is cheaper than defending in rebuttal.
   - *Alternative:* POST-SUBMIT if revision bandwidth is zero; add one line at rebuttal if raised.

2. **`jia2025damagedrivers`** -- IJDRR 2025. CA-specific interpretable ML for CAL FIRE damage drivers (Jan 2025 S. CA test set).
   - **Recommendation:** CITE-NOW in Section 2 Line A with a single explicit differentiator: "damage drivers (post-ignition) vs. ignition prediction (ours)". Two CA + CAL FIRE + interpretable-ML papers on the same arXiv listing without differentiation will confuse reviewers.

---

---

## Line B -- CITE-NOW (4)

1. **`xie2025marsha`** -- npj Climate Action 4:70 (2025); arXiv:2504.17200 -- Section 2 Line B + Section 4 (architecture comparison).
   - *Why:* Peer-reviewed 2025 successor to the `xie2025wildfiregpt` cite we already carry. Same lead author, multi-agent RAG for natural hazards.
   - *How:* Replace `xie2025wildfiregpt` with `xie2025marsha` (or cite both, noting MARSHA is the peer-reviewed evolution); contrast FireFair's three-agent EJ-audited design vs. MARSHA's 4-agent decision-support design.

2. **`markov2025firescope`** -- arXiv:2511.17171 -- Section 2 Line B + Section 4 (Sentinel-2 VLA).
   - *Why:* **Closest 2025 peer to FireFair's Sentinel-2 VLA.** Couples Sentinel-2 + climate + expert risk rasters with language-model CoT reasoning; demonstrates US->EU cross-continental transfer.
   - *How:* Cite prominently in Line B and in the VLA methods section. Clarify FireFair differences: CA-local daily ignition (vs. their continental transfer) and explicit EJ audit (they do not compute DeltaEO / rho).

3. **`chen2025gal`** -- arXiv:2510.12061 -- Section 2 Line B + Section 4 (Equity Agent).
   - *Why:* Direct conceptual competitor to our Equity Agent's geospatial grounding.
   - *How:* Cite in Line B; explicit sentence differentiating FireFair's quantitative SVI-quartile EJ audit from GAL's descriptive grounding.

4. **`esparza2025damagevlm`** -- arXiv:2509.01895 -- Section 2 Line B (also could cite in Section 1 intro next to the Jan-2025 fires).
   - *Why:* Same 2025 Eaton + Palisades fires we feature; same VLM-for-wildfire paradigm; different modality (ground imagery vs. satellite).
   - *How:* One sentence distinguishing ground-level zero-shot damage assessment (theirs) from Sentinel-2 risk analysis (ours).

## Line B -- DISCUSS (4)

1. **`irvin2025teochat`** (TEOChat, ICLR 2025; arXiv:2410.06234). Temporal-EO VLM baseline.
   - **Recommendation:** CITE-NOW in Section 2 Line B, one sentence as the temporal-EO VLM baseline FireFair's VLA implicitly inherits from.

2. **`danish2025geobench`** (GEOBench-VLM, ICCV 2025; arXiv:2411.19325). Best VLM ~42% MCQ on geospatial tasks.
   - **Recommendation:** CITE-NOW as quantitative motivation for multi-agent orchestration (raw VLM is brittle). One sentence. High defensive value.

3. **`qi2026smokebench`** (SmokeBench, WACV 2026; arXiv:2512.11215). GPT-4o / Gemini / Qwen all fail at early smoke localization.
   - **Recommendation:** CITE-NOW in the VLA motivation paragraph. One sentence. Pairs well with GEOBench-VLM.

4. **`szwarcman2024prithvi`** (Prithvi-EO-2.0, arXiv:2412.02732). HLS/Sentinel-2 foundation model.
   - **Recommendation:** If the VLA is fine-tuned from a generic VLM, **cite Prithvi-EO-2.0 in the architecture section with one sentence** acknowledging it as the RS-native alternative; otherwise POST-SUBMIT. Low cost either way.

---

## Updated quick priorities (after Lines A + B)

- **Highest-value single edit:** replace `xie2025wildfiregpt` with `xie2025marsha` in every existing draft citation. Mandatory update.
- **Most defensive edit:** add one paragraph on `markov2025firescope` in Line B. The overlap with our Sentinel-2 VLA is too close to ignore.
- **Cheapest high-leverage edits:** one sentence each for TEOChat, GEOBench-VLM, SmokeBench (all three together = ~3 sentences, ~45 min of prose).
- **New coverage gap visible at Line B** (to reinforce in Limitations): no 2025/26 VLM-for-wildfire paper computes any fairness / EJ metric. FireScope, GAL, MARSHA, Esparza, GEOBench-VLM -- none are EJ-audited. FireFair's Equity Agent stands alone in the VLM-wildfire neighbourhood.

---

## Line C -- CITE-NOW (5)

Line C was biased-hard per your instructions. These are the five where omission is the biggest reviewer-pushback risk.

1. **`huynh2024mitigating`** -- Nat. Machine Intelligence 2024 -- Section 2 Line C + Section 5 (Equity metrics).
   - *Why:* Closest peer-reviewed methodological analog to our DeltaEO / rho audit. Shows an EJ tool's parameter-sensitivity had \$2.08B allocative consequences.
   - *How:* Cite as the nearest cousin to our audit; two sentences noting "we adapt the allocative-sensitivity idea to a predictive-model setting."

2. **`saxena2024spatial`** -- arXiv:2403.14040 -- Section 5 (metric definition) + Limitations.
   - *Why:* Position paper that catalogues spatial-fairness failure modes. Cite *defensively* to pre-empt the strongest reviewer critique: "DeltaEO does not provably reduce discrimination on protected attributes."
   - *How:* One sentence at metric definition: acknowledge this is an open problem and that our contribution is a working operationalization, not a solved one.

3. **`vargo2023social`** -- AJPH 2023 -- Section 2 Line C (equity motivation).
   - *Why:* Canonical SVI + wildfire-smoke paper; appears in every EJ-wildfire Related Work. Omission signals unfamiliarity.
   - *How:* Cite alongside `dennin2025smokejustice` and `modaresirad2023social` as the third pillar.

4. **`pollack2024flood`** -- Nat. Sustainability 2024 -- Section 2 Line C + Section 5.
   - *Why:* Methodological analog in flood-risk management; Nature-family journal. Gives us a cross-hazard precedent for DeltaEO / rho, defending against "this is wildfire-specific ad hoc" critique.
   - *How:* One sentence positioning FireFair's equity metrics within a broader hazard-equity measurement tradition.

5. **`barocas2023fairml`** -- Barocas/Hardt/Narayanan textbook -- Section 5 (DeltaEO definition footnote).
   - *Why:* Our DeltaEO derives from Hardt/Price/Srebro 2016 (Ch. 3). Citing the textbook signals EJ-aware framing for AIES / FAccT reviewers.
   - *How:* Single citation at the DeltaEO equation. Zero narrative cost.

## Line C -- DISCUSS (4)

1. **`salazarmiranda2024redlining`** -- Nature Cities 2024. Long-term redlining -> climate-risk disparity.
   - **Recommendation:** **CITE-NOW in Section 1 or Section 2 Line C**, one sentence, if FireFair frames its EJ audit as connecting ML predictions to historical structural-racism patterns. Strong framing value.

2. **`letellier2025grf`** -- Environment International 2025. GRF on CA wildfire smoke subpopulation vulnerability.
   - **Recommendation:** CITE-NOW in Line C, one sentence, as the closest 2025 CA+ML+health-vulnerability peer. Under-75 and Black subpopulations are the high-vulnerability groups their paper identifies -- that directly informs our SVI-quartile analysis.

3. **`cai2025fairearth`** -- FAIR-Earth (arXiv:2502.06831). INR fairness for Earth data.
   - **Recommendation:** DISCUSS -> lean POST-SUBMIT unless we can add a short sentence saying "our Sentinel-2 VLA does not audit representation-level fairness; that is orthogonal (see Cai & Balestriero 2025) and future work." High defensive value if we touch it; can wait otherwise.

4. **`ghamisi2024responsibleai`** -- IEEE GRSM 2025 (accepted). Responsible AI for EO survey.
   - **Recommendation:** DISCUSS -> lean POST-SUBMIT. Only cite if we explicitly invoke "responsible AI" framing; otherwise the survey-level general coverage is cheap to skip.

---

## Updated quick priorities (all three lines)

**Before 2026-05-17 deadline (30 days):**

- **Mandatory updates (2):**
  1. Replace `xie2025wildfiregpt` with `xie2025marsha` (npj Climate Action 2025 peer-reviewed evolution). Affects every existing draft citation.
  2. Add `markov2025firescope` to Section 2 Line B and Section 4 -- the closest 2025 peer to our Sentinel-2 VLA; must be differentiated explicitly.

- **High-leverage CITE-NOW edits (total ~12):** Lines A (3), B (4), C (5). Estimated revision cost: one paragraph addition to Section 2 + two sentences in Section 5 + refreshing the Section 3 datasets paragraph.

- **One-sentence-each DISCUSS-lean-CITE-NOW (6):** `kondylatos2025uncertainty`, `jia2025damagedrivers`, `irvin2025teochat`, `danish2025geobench`, `qi2026smokebench`, `salazarmiranda2024redlining`. Estimated cost: ~45 min of prose.

- **Optional DISCUSS you can skip without reviewer risk (4):** `szwarcman2024prithvi`, `letellier2025grf`, `cai2025fairearth`, `ghamisi2024responsibleai`.

**Single biggest defensive paragraph to write** (for Limitations): "No prior wildfire-prediction ML model has been audited with equal-opportunity or per-capita disparate-exposure metrics. FireFair is, to our knowledge, the first; we acknowledge this means our metrics lack an established benchmark, and we cite `saxena2024spatial` as the closest conceptual predecessor and `huynh2024mitigating` + `pollack2024flood` as audits of adjacent EJ policy / flood-risk systems." This paragraph alone will preempt 60% of the fairness-reviewer questions you would otherwise face.

