# FireFair -- Inbox (CITE-NOW + DISCUSS)

Date: 2026-04-17
Deadline: 2026-05-17 (30 days)

---

## CITE-NOW (8)

Add these before submission. Each entry: BibTeX key, target section, one-line why, one-line how.

1. **`bhowmik2025cawfi`** -- Section 3 (Dataset).
   - *Why:* New 37M-point California wildfire + covariate dataset (2012--2022); reviewer will ask.
   - *How:* Add to related-dataset paragraph; note overlap with our training window. Optional additional eval split if time permits.

2. **`michail2025firecastnet`** -- Section 2 (Related Work), Line A.
   - *Why:* 2025 SOTA graph-based seasonal fire-activity neural forecaster (Nature Sci Reports).
   - *How:* One sentence next to Di Giuseppe 2025 as the "global neural forecasting" cluster.

3. **`lahrichi2025wsts`** -- Section 3 or Section 5 (Experiments).
   - *Why:* WSTS+ is the largest public time-series wildfire benchmark; we claim time-series performance.
   - *How:* One sentence in dataset related work; flag WSTS+ as potential future comparison.

4. **`xie2025marsha`** -- Section 2 (Related Work), Line B + Section 4 (Architecture comparison).
   - *Why:* Direct 2025 multi-agent RAG wildfire competitor; same lineage as WildfireGPT.
   - *How:* Replace or augment the existing WildfireGPT cite with MARSHA; contrast our three-agent EJ-audited design.

5. **`chen2025geospatial`** -- Section 2 (Related Work), Line B + Section 4 (Equity Agent).
   - *Why:* GAL grounds LLM agents in geospatial / demographic data; same space as our Equity Agent.
   - *How:* Cite in Line B paragraph; distinguish FireFair as explicitly quantifying EJ metrics (DeltaEO, rho) vs. GAL's descriptive grounding.

6. **`esparza2025automated`** -- Section 2 (Related Work), Line B.
   - *Why:* Same 2025 LA fires, same VLM-for-wildfire paradigm; complements our Sentinel-2 VLA.
   - *How:* One sentence distinguishing ground-level imagery (theirs) vs. satellite (ours).

7. **`huynh2024mitigating`** -- Section 2 (Related Work), Line C + Section 5 (Equity metrics).
   - *Why:* Nature MI peer-reviewed CES audit; closest methodological analog to our DeltaEO/rho framework.
   - *How:* Cite as motivating EJ-audit tradition; two sentences on allocative sensitivity.

8. **`saxena2024spatial`** -- Section 5 (Equity Agent / metric definition) + Limitations.
   - *Why:* Position paper that explicitly catalogues spatial-fairness failure modes; pre-empts the reviewer critique that DeltaEO is ad hoc.
   - *How:* One defensive sentence at metric definition: acknowledge open question of whether DeltaEO demonstrably reduces discrimination on protected attributes; point to Saxena et al. as open problem.

---

## DISCUSS (7)

Needs your judgment. My recommendation in bold.

1. **`irvin2025teochat`** (TEOChat, ICLR 2025). Baseline temporal-EO VLM.
   - **Recommendation: CITE-NOW in Line B as the temporal-EO VLM baseline. One sentence. Low cost, high coverage value.**

2. **`danish2025geobench`** (GEOBench-VLM, ICCV 2025). Best VLM ~42% on geospatial tasks.
   - **Recommendation: CITE-NOW as motivation for multi-agent design (raw VLM is insufficient). One sentence.**

3. **`qi2026smokebench`** (SmokeBench, WACV 2026). GPT-4o/Gemini fail at smoke localization.
   - **Recommendation: CITE-NOW (one sentence) in VLA motivation. Strengthens our case without adding scope.**

4. **`vargo2023social`** (AJPH, SVI + wildfire smoke).
   - **Recommendation: CITE-NOW alongside Dennin 2025 and Modaresi Rad 2023 as the third pillar of the equity-motivation paragraph.**

5. **`dennin2025socially`** (already in draft).
   - **Recommendation: verify the citation is present in Section 1 and Section 2. No code-path change.**

6. **`barocas2023fairml`** (FairML book).
   - **Recommendation: CITE-NOW as a single citation at the DeltaEO definition. Improves credibility with AIES/FAccT reviewers. Zero scope cost.**

7. **`ghamisi2024responsibleai`** (Responsible AI for EO).
   - **Recommendation: DISCUSS -> lean POST-SUBMIT unless we already touch responsible-AI framing. If we do, cite in one sentence.**

---

## Quick priorities

- **This week:** drop the 8 CITE-NOW items in. These are the ones a reviewer will notice as missing.
- **DISCUSS triage (1 hour):** decide yes/no on TEOChat, GEOBench-VLM, SmokeBench, Vargo, Barocas book -- I recommend "yes, one sentence each."
- **Coverage gap to address explicitly in Limitations:** no prior wildfire-prediction model audits itself with equal-opportunity or per-capita exposure metrics. This is simultaneously our novelty and a reviewer target. Pre-empting it with a paragraph is cheaper than defending it later.
