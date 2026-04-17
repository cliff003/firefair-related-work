# FireFair -- Initial Related-Work Sweep

- Date: 2026-04-17
- Submission deadline: 2026-05-17 (ACM GoodIT 2026)
- Baseline bibliography: `firefair_existing.bib`
- New candidates appended: `candidates.bib`

## Counts

By Action:

| Action       | Count |
|--------------|-------|
| CITE-NOW     |  8    |
| DISCUSS      |  7    |
| POST-SUBMIT  | 13    |
| WATCH        |  2    |

By Line:

| Line                              | Kept |
|-----------------------------------|------|
| A -- ML wildfire prediction       | 12   |
| B -- LLM agents + VLM for hazard  | 14   |
| C -- EJ / spatial fairness        | 17   |
| draft-only (included in bib)      |  3   |

Note: some papers cross lines (e.g., FireScope is A+B, MARSHA is B+C).

---

## CITE-NOW

Reviewers will ask about these. Add before the 2026-05-17 deadline.

### 1. Bhowmik et al. 2025, CAWFI [A-predict] [dataset]
- **BibTeX key:** `bhowmik2025cawfi` (arXiv:2509.11015)
- **Takeaway:** 37M-point daily California wildfire + meteorology + vegetation dataset covering 2012--2022, explicitly built for AI predictive modeling.
- **Relation to FireFair:** Direct overlap with our California-only training window. A reviewer will ask why we did not benchmark on CAWFI.
- **Target section:** Section 3 (Dataset) -- at minimum in related-dataset paragraph, ideally as an additional evaluation split.

### 2. Michail et al. 2025, FireCastNet [A-predict] [baseline]
- **BibTeX key:** `michail2025firecastnet` (Sci. Reports; arXiv:2502.01550)
- **Takeaway:** Graph-based Earth-as-a-graph model for seasonal (up to 6-month) burned-area forecasting on SeasFire.
- **Relation to FireFair:** Strong baseline for the "global-scale neural fire forecasting" narrative; complements Di Giuseppe 2025. Not our direct competitor (seasonal, not ignition), but refusing to cite it will look like an oversight.
- **Target section:** Section 2 (Related Work), Line A paragraph.

### 3. Lahrichi et al. 2025, WSTS+ benchmark [A-predict] [dataset]
- **BibTeX key:** `lahrichi2025wsts` (arXiv:2502.12003)
- **Takeaway:** New time-series next-day-wildfire-spread benchmark (doubles WFTS years, adds 2016/17/22/23); SwinUnet is SOTA.
- **Relation to FireFair:** We claim strong time-series performance; a reviewer will ask whether we tried the public TS wildfire benchmark.
- **Target section:** Section 3 or Section 5 (Experiments).

### 4. Xie et al. 2025, MARSHA / WildfireGPT-2 [B-agent-vlm] [baseline]
- **BibTeX key:** `xie2025marsha` (npj Climate Action; arXiv:2504.17200)
- **Takeaway:** Multi-agent RAG system for hazard adaptation; same lineage as WildfireGPT, with task-orchestrator / user-profile / planning / analyst agents.
- **Relation to FireFair:** Our most direct architectural competitor for "LLM multi-agent + wildfire." If cited only via WildfireGPT, we miss the 2025 evolution.
- **Target section:** Section 2 (Related Work), Line B paragraph; Section 4 (Architecture) contrast table.

### 5. Chen et al. 2025, GAL for wildfire response [B-agent-vlm] [baseline]
- **BibTeX key:** `chen2025geospatial` (arXiv:2510.12061)
- **Takeaway:** Geospatial Awareness Layer that grounds LLM agents in infrastructure / demographic / terrain / weather data for wildfire response.
- **Relation to FireFair:** Direct conceptual competitor to our Equity Agent's geospatial grounding. Must be distinguished from FireFair's explicit SVI-quartile equity audit.
- **Target section:** Section 2 (Related Work) and Section 4 (Equity Agent).

### 6. Esparza et al. 2025, Wildfire damage VLM on 2025 Palisades [B-agent-vlm] [baseline]
- **BibTeX key:** `esparza2025automated` (arXiv:2509.01895)
- **Takeaway:** Zero-shot VLM + LLM pipeline for wildfire damage classification on 2025 Eaton/Palisades ground imagery.
- **Relation to FireFair:** Uses the same 2025 LA fires we highlight; same VLM-for-wildfire paradigm; different modality (ground imagery vs. our Sentinel-2).
- **Target section:** Section 2 (Related Work), Line B paragraph.

### 7. Huynh et al. 2024, CalEnviroScreen algorithmic audit [C-equity] [method]
- **BibTeX key:** `huynh2024mitigating` (Nature Machine Intelligence)
- **Takeaway:** Full audit of CalEnviroScreen under EJ lens; shows allocative sensitivity to subjective model specs and $2.08B funding consequence.
- **Relation to FireFair:** Nearest peer-reviewed article to our DeltaEO/rho framing. A fairness-aware reviewer will ask why we did not model allocative uncertainty. Also validates our choice to cross-check SVI with CES-style indices.
- **Target section:** Section 2 (Related Work), Line C paragraph; Section 5 (Equity metrics).

### 8. Saxena et al. 2024, Spatial Fairness position paper [C-equity] [method]
- **BibTeX key:** `saxena2024spatial` (arXiv:2403.14040)
- **Takeaway:** Position paper arguing spatial fairness is under-defined; catalogues how existing methods fail to close the loop between location's correlation with protected attributes and actual discrimination reduction.
- **Relation to FireFair:** Directly challenges DeltaEO / rho. Citing it defensively lets us pre-empt the strongest reviewer critique: "your fairness metric does not provably reduce discrimination on protected attributes."
- **Target section:** Section 5 (Equity Agent / metrics definitions); brief acknowledgement in Limitations.

---

## DISCUSS

Needs your judgment -- I've included a recommendation per item.

### 1. Irvin et al. 2025, TEOChat (ICLR 2025) [B-agent-vlm] [baseline]
- `irvin2025teochat` (arXiv:2410.06234). Temporal Earth-observation VLM; outperforms GPT-4o / Gemini 1.5 Pro on change detection / temporal VQA.
- **Rationale:** Most-cited 2025 temporal-EO VLM baseline. Our Sentinel-2 Vision-Language Agent inherits the temporal-multi-image setting. Not a direct wildfire competitor but a must-know baseline for the Line B reviewer.
- **Recommendation:** CITE-NOW in Section 2 Line B as the baseline temporal-EO VLM. Low revision cost -- one sentence.

### 2. Danish et al. 2025, GEOBench-VLM (ICCV 2025) [B-agent-vlm] [benchmark]
- `danish2025geobench` (arXiv:2411.19325). Shows best geospatial VLM gets only ~42% MCQ accuracy across 31 geospatial tasks.
- **Rationale:** Strongest evidence that geospatial VLMs are brittle -- supports our framing that a hazard-grounded agent pipeline is needed beyond a raw VLM call.
- **Recommendation:** CITE-NOW in Section 2 Line B as motivation; tension pairs nicely with our VLM-agent approach. Low cost.

### 3. Qi et al. 2025, SmokeBench (WACV 2026) [B-agent-vlm] [benchmark]
- `qi2026smokebench` (arXiv:2512.11215). Shows GPT-4o / Gemini-2.5 Pro / Qwen2.5-VL all fail at early-stage smoke localization.
- **Rationale:** Quantitative evidence that MLLMs alone are insufficient for wildfire smoke tasks -- a strong motivator for FireFair's agent orchestration.
- **Recommendation:** CITE-NOW (one sentence) in Line B motivation. Low cost, high defensive value.

### 4. Vargo et al. 2023, SVI + wildfire smoke 2011--2021 (AJPH) [C-equity]
- `vargo2023social`.
- **Rationale:** This is the canonical SVI + wildfire-smoke epidemiology paper; it is cited in every EJ-wildfire related-work paragraph. Omitting it signals unfamiliarity with the literature.
- **Recommendation:** CITE-NOW alongside Dennin/Modaresi Rad as a third pillar in the equity-motivation paragraph. Very low cost.

### 5. Dennin et al. 2025 (already draft-known) but needs explicit verification [C-equity]
- `dennin2025socially`. Already in draft -- confirmed published March 2025.
- **Rationale:** Not actionable beyond verifying the citation is present in Section 1 / Section 2.
- **Recommendation:** Verify, keep. No code-path change.

### 6. Barocas, Hardt, Narayanan 2023, FairML book [C-equity] [method]
- `barocas2023fairml`.
- **Rationale:** Foundational -- our DeltaEO metric derives from Hardt/Price/Srebro 2016 equal-opportunity notion, which is chapter 3 of this book. Citing the book rather than (only) the 2016 paper signals EJ-aware framing.
- **Recommendation:** CITE-NOW as a single citation in Section 5 (metric definition). Low cost, improves credibility with AIES / FAccT-style reviewers.

### 7. Ghamisi/Gevaert et al. 2024, Responsible AI for EO [C-equity]
- `ghamisi2024responsibleai` (arXiv:2405.20868).
- **Rationale:** Covers fairness / bias in EO explicitly; cited by FAIR-Earth (Cai & Balestriero) and EU-AI-Act-auditing work. Signals that we know the EO-fairness literature.
- **Recommendation:** DISCUSS -> lean POST-SUBMIT if revision budget is tight, CITE-NOW if it fits in one sentence in Line C.

---

## POST-SUBMIT (grouped by line)

### Line A
- `anastasiou2025wildfire` -- ViT/CNN burned-area forecast Mediterranean (arXiv:2505.17556).
- `kondylatos2025uncertainty` -- Deep ensemble uncertainty for wildfire danger (arXiv:2509.25017).
- `chen2025realtime` -- Real-time multimodal transformer wildfire system (arXiv:2503.05971).
- `zhou2025comparative` -- CNN vs Transformer (Cheng group) on NDWS (arXiv:2503.14150).
- `erzibengoa2025iberfire` -- IberFire Spain dataset (arXiv:2505.00837).
- `markov2025firescope` -- FireScope CoT oracle (arXiv:2511.17171); A+B crossover.
- `adversarial2024wildfire` -- Adversarial robustness for wildfire models (arXiv:2412.20006).

### Line B
- `kuckreja2024geochat` -- GeoChat, foundational RS VLM baseline (CVPR 2024).
- `falcon2025vlm` -- Falcon RS VLM foundation (arXiv:2503.11070).
- `li2025vlmrs_survey` -- VLM-for-RS survey (arXiv:2505.14361).
- `ayanzadeh2026wildfirevlm` -- WildfireVLM (arXiv:2602.13305); very recent.
- `climateagent2025` -- ClimateAgent orchestrator (arXiv:2511.20109).
- `multitarget2026wildfire` -- Multi-target wildfire + LLM synthesis PoC (arXiv:2601.11686).
- `gao2025instructor` -- Instructor-Worker LLM for LA wildfire air quality (arXiv:2503.00566); would be CITE-NOW if revision budget allowed, but scope is air-quality-analysis not ignition prediction.
- `contextaware2026mas` -- Context-Aware MAS for wildfire (Sensors 2026); also borderline CITE-NOW but still undergoing verification.

### Line C
- `jonesngo2025compound` -- Compound wildfire smoke + heat California (Earth's Future 2025).
- `jung2024advancing` -- CHVI for wildland fire smoke (STOTEN 2024).
- `franchi2023algorithms` -- EJ lens on algorithmic audits (FAccT 2023).
- `cai2025nolocation` -- FAIR-Earth (arXiv:2502.06831).
- `salazarmiranda2024redlining` -- Redlining x climate risk (Nature Cities 2024).
- `wildlandpm2025disproportionate` -- Wildland fire PM2.5 disparities (ACS ES&T Air 2025).
- `fleishman2024vulnerability` -- Minorities + wildfires California.
- `chen2023geography` -- SVI + wildfire occurrence 1984--2018.

---

## WATCH

- `shahabi2023fairspatial` -- Fair Spatial Indexing (VLDB / arXiv:2302.02306). Useful only if we move toward spatial-index-level fairness mitigation in a journal extension.
- ECMWF / Di Giuseppe follow-up (Nature Comms April 2025) -- already cited, but track for a supplementary release.

---

## Coverage Gaps

**This is the section that matters most for reviewer-pushback risk.**

1. **No paper directly audits a wildfire prediction ML model for equal-opportunity or per-capita disparate-exposure.** Every EJ-wildfire paper I found is descriptive epidemiology (Vargo, Modaresi Rad, Dennin, Jung, Jones-Ngo) using SVI/CES as a covariate or stratifier, *not* as a fairness constraint on a predictive model. FireFair is, as far as this sweep shows, the first hazard-prediction paper to compute DeltaEO and rho on an ignition model. That is both a contribution and a vulnerability: a FAccT-style reviewer can argue we have no prior-art benchmark for our metric.
    - **Mitigation:** (a) cite `saxena2024spatial` as the closest conceptual predecessor and explicitly acknowledge the gap; (b) cite `huynh2024mitigating` as the analog audit of a policy (not predictive) EJ model; (c) cite Hardt/Price/Srebro 2016 via `barocas2023fairml`.

2. **Spatial-fairness literature is almost entirely theoretical/positional.** `saxena2024spatial` and `shahabi2023fairspatial` both argue for the importance of spatial fairness without demonstrating it on hazard data. There is no SOTA comparator for rho (per-capita alert exposure ratio) in the wildfire setting.
    - **Risk:** Reviewers may claim rho is ad hoc. **Mitigation:** frame rho against disparate-impact ratio / 80% rule tradition (EEOC), not against a wildfire-specific prior.

3. **Spatial-fairness on non-wildfire hazards (flood, heat, air quality) is sparse and recent.** Despite searching, I found no strong flood-equity ML paper with a formalized fairness metric. The closest are urban-prediction GNNs (`2501.11214`) that reduce spatial disparity without ties to protected attributes. Our DeltaEO transfers cleanly but has no established neighbor.
    - **Risk:** Reviewers may ask "how does this transfer to flood / heat?" **Mitigation:** add a one-paragraph generality discussion citing `saxena2024spatial` and `cai2025nolocation`.

4. **FAccT / EAAMO 2024 and 2025 have minimal wildfire-specific content.** I found `franchi2023algorithms` but nothing directly on hazard-prediction fairness. This is partly by field drift -- wildfire equity lives in AJPH / Nature Comms Earth&Env / Science Advances rather than ML-fairness venues. That cultural gap is itself a finding: FireFair is one of very few works bridging hazard ML and the ML-fairness community.

5. **VLM-for-EJ specifically is non-existent.** No paper I found combines Sentinel-2 / VLM / EJ audit. Our Equity Agent is novel here, but that also means no direct baseline. Expect reviewers to ask why we did not ablate against a plain GeoChat/TEOChat + SVI post-hoc overlay.
    - **Mitigation:** add an ablation (GeoChat + SVI vs. Equity Agent) if time permits; otherwise acknowledge explicitly.

6. **Time-series augmentation (CutMix) on wildfire time series has not been published in 2025.** `bhowmik2025cawfi` is the closest California dataset with no CutMix evaluation, and the InceptionTime + CutMix combination has only been empirically studied on ECG/EEG/HAR. This makes our combo genuinely novel but also under-validated externally.
    - **Mitigation:** frame this as contribution #1 in the ablation narrative; not a citation gap.

7. **Minor: no directly competing three-agent wildfire architecture.** The closest are MARSHA (4 agents, text-only), GAL (LLM + geo grounding), and Context-Aware MAS (orchestrator + VQA). None of them compute DeltaEO or rho. FireFair's novelty is specifically the EJ-audited agent, which is unchallenged in the literature I scanned.
