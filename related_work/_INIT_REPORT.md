# FireFair -- Initial Related-Work Sweep (full re-sweep)

- Date: 2026-04-17
- Submission deadline: 2026-05-17 (ACM GoodIT 2026, 30 days)
- Baseline bibliography: `firefair_existing.bib` (read-only)
- New candidates appended: `candidates.bib`
- Status: **All three lines complete.**

## Counts

By Action:

| Action       | Line A | Line B | Line C | Total |
|--------------|-------:|-------:|-------:|------:|
| CITE-NOW     |      3 |      4 |      5 |    12 |
| DISCUSS      |      2 |      4 |      4 |    10 |
| POST-SUBMIT  |      7 |      5 |      7 |    19 |
| WATCH        |      1 |      1 |      1 |     3 |
| **Line total**|     13 |     14 |     17 |    44 |

Plus 3 draft-promoted entries (Dennin, Ji, Modaresi Rad) carried in `candidates.bib` independently of the sweep counts.

By relevance tag (approximate, some papers cross-tag):

| Tag           | Count |
|---------------|-------|
| [A-predict]   |   13  |
| [B-agent-vlm] |   14  |
| [C-equity]    |   17  |
| [dataset]     |    8  |
| [baseline]    |   12  |
| [method]      |    6  |

---

## Line A -- ML wildfire ignition / risk prediction

Lookback: 12 months (since 2025-04-17). Deduped against `firefair_existing.bib` (which already contains `digiuseppe2025global`, `jain2020review`, `mathur2025firecastrl`, `xu2025bcwildfire`, `fawaz2020inceptiontime`).

Kept: **11 new papers** + 3 draft-promoted (Dennin, Ji, Modaresi Rad -- categorically Line C but included in bib now).

### CITE-NOW (3)

#### 1. Bhowmik et al. 2025, CAWFI [A-predict] [dataset]
- **Key:** `bhowmik2025cawfi` (arXiv:2509.11015, 2025-09-14)
- **Takeaway:** 37M-point California-only wildfire + weather + vegetation + topo dataset spanning 2012-2022, purpose-built for AI predictive modelling; reports 85.7% recall on >300k-acre fires with a spatio-temporal AI baseline.
- **Relation to FireFair:** Direct overlap with our CA training window. A reviewer will ask why we didn't benchmark on CAWFI. Even if we don't retrain, a one-sentence mention and justification is mandatory.
- **Target section:** Section 3 (Dataset) and Section 2 (Related Work Line A).

#### 2. Michail et al. 2026, FireCastNet [A-predict] [baseline]
- **Key:** `michail2026firecastnet` (Sci Reports 16:1006, 2026; arXiv:2502.01550 v2 2025-11-19)
- **Takeaway:** Peer-reviewed Nature Sci Reports paper combining 3D conv with GraphCast-style GNN on the SeasFire cube; up to 6-month burned-area forecast; beats GRU and ConvLSTM in fire-prone regions.
- **Relation to FireFair:** Nearest 2025/26 peer to `digiuseppe2025global`. We already cite Di Giuseppe -- omitting FireCastNet will look like an oversight. Not a direct competitor (global seasonal vs. our CA daily ignition), but must be positioned.
- **Target section:** Section 2 (Related Work Line A).

#### 3. Prapas et al. 2025, TeleViT1.0 [A-predict] [baseline]
- **Key:** `prapas2025televit` (arXiv:2512.00089, 2025-11-26)
- **Takeaway:** Vision Transformer with multi-scale local/global views and ocean-climate teleconnection indices; outperforms baselines at every lead time on subseasonal-to-seasonal fire pattern forecasting.
- **Relation to FireFair:** Grouped with FireCastNet as the 2025 "transformer + graph" S2S fire-forecast cohort. We differ in target (daily CA ignition), but the reviewer trail from Papoutsis/Camps-Valls is strong.
- **Target section:** Section 2 (Related Work Line A).

### DISCUSS (2)

#### 1. Kondylatos et al. 2025, Uncertainty-Aware DL for Wildfire Danger [A-predict] [method]
- **Key:** `kondylatos2025uncertainty` (arXiv:2509.25017, 2025-09-29)
- **Takeaway:** Combines epistemic + aleatoric uncertainty on wildfire-danger forecasting; +2.3% F1 and -2.1% ECE vs. deterministic baseline.
- **Rationale:** FireFair reports point probabilities without UQ bounds. A fairness-aware reviewer can argue that EJ audits without uncertainty bars understate disparities. This is the kind of gap that's cheap to pre-empt in Limitations.
- **Recommendation:** **CITE-NOW in Limitations only -- one sentence.** Acknowledge UQ as a natural extension; do not add UQ to the model.

#### 2. Jia & Opabola 2025, CA wildfire damage drivers [A-predict]
- **Key:** `jia2025damagedrivers` (IJDRR 126:105610, 2025; DOI:10.1016/j.ijdrr.2025.105610)
- **Takeaway:** Interpretable ML on CAL FIRE damage-inspection data 2013-2024; DNN + transfer learning + SHAP; tested on Jan 2025 Southern California fires.
- **Rationale:** Overlaps our CA + CAL FIRE + interpretable-ML pitch but targets *post-ignition structural damage*, not ignition probability. If unexplained, reviewers will conflate.
- **Recommendation:** **CITE-NOW in Section 2 Line A** with an explicit one-sentence task-framing differentiator: "damage drivers (post-ignition) vs. ignition probability (ours)."

### POST-SUBMIT (7)

Grouped by sub-theme; one-liner each.

- `anastasiou2025spread` (arXiv:2505.17556, May 2025) -- Mediterranean 2006-2022 burned-area ViT/CNN; best window -4 to +5 days around ignition.
- `zhou2025spread` (JGR ML&C 2025; arXiv:2503.14150) -- CA remote-sensing spread CNN vs Transformer; Swin-UNet wins (Cheng group).
- `zheng2025firebreaks` (EGUsphere 2025) -- ConvLSTM with human-intervention firebreaks; three CA case studies (Cheng group).
- `xu2025generative` (arXiv:2506.02485, Jun 2025) -- LLM-driven lit review + framework for GAN/VAE/diffusion wildfire spread prediction.
- `seydi2025alphaearth` (arXiv:2509.07852, Sep 2025) -- Bi-temporal Siamese + AlphaEarth for burned-area mapping; 95% accuracy.
- `karasante2025seasfire` (Sci Data 12:368, 2025) -- SeasFire cube dataset (global, 59 vars, 2001-2021); pairs with FireCastNet/TeleViT.
- `zhao2025exebench` (arXiv:2505.08529, May 2025) -- ExEBench foundation-model benchmark including wildfire.

### WATCH (1)

- `bhardwaj2025containment` (arXiv:2512.09835, Dec 2025) -- CA containment-time regression; downstream task. Track only in case deadline slips and we add a downstream-task paragraph.

### Line A Coverage Gaps (preliminary)

1. **Zero 2025/26 papers apply CutMix-style augmentation to wildfire time series.** CutMix + time-series work (TSCMamba et al.) is on ECG/EEG/HAR. This validates FireFair's novelty on the augmentation axis but also means no external empirical precedent -- reviewer may ask for ablation against Manifold Mixup / cut-paste alternatives.
2. **InceptionTime backbone is aging.** 2025 competitors are moving to (a) GNN on Earth-as-a-graph (FireCastNet), (b) ViT with teleconnections (TeleViT), or (c) selective-state-space models (TSCMamba in general TSC). Expected reviewer question: *"why not Mamba?"* A one-sentence justification (parameter efficiency, strong TSC track record, fits CA daily meteorology dimensionality) is cheap insurance.
3. **Most 2025 CA-specific work targets spread, damage, or containment -- not ignition.** Jia-Opabola (damage), Zhou-Cheng (spread), Zheng-Cheng (spread + firebreaks), Bhardwaj (containment). CAWFI is the exception and the only CA-wide ignition-relevant 2025 dataset; re-emphasises why citing it is non-negotiable.
4. **No 2025 paper combines ignition prediction with fairness or EJ auditing on meteorological time series.** That gap is the FireFair contribution; flagged here so it reappears in the final Coverage-Gaps consolidation after Line C.

---

## Line B -- LLM agents + VLM for remote sensing / hazard

Lookback: 18 months (since 2024-10-17). Deduped against `firefair_existing.bib` (which already contains `xie2025wildfiregpt` -- note MARSHA below is the peer-reviewed 2025 successor by the same lead author).

Kept: **13 new papers.**

### CITE-NOW (4)

#### 1. Xie et al. 2025, MARSHA [B-agent-vlm] [baseline]
- **Key:** `xie2025marsha` (npj Climate Action 4:70, 2025; arXiv:2504.17200)
- **Takeaway:** Peer-reviewed RAG-based multi-agent LLM for natural hazard decision support; same lead author as `xie2025wildfiregpt`; evaluated on ten expert case studies.
- **Relation to FireFair:** This is the 2025 evolution of the WildfireGPT we currently cite. Omitting it (or continuing to cite only the 2024 arXiv) will look like we missed the peer-reviewed publication from the same group.
- **Target section:** Section 2 Line B (replace or augment existing `xie2025wildfiregpt` cite); Section 4 architecture contrast.

#### 2. Markov et al. 2025, FireScope [B-agent-vlm] [baseline]
- **Key:** `markov2025firescope` (arXiv:2511.17171, 2025-11-21)
- **Takeaway:** First framework to combine Sentinel-2 imagery + climate covariates + expert wildfire risk rasters + language-model chain-of-thought reasoning; trained US, tested EU.
- **Relation to FireFair:** **The closest 2025 peer to our Sentinel-2 Vision-Language Agent.** Our defensibility depends on (a) citing FireScope, and (b) clearly staking out our differences: CA-local daily ignition (vs. their cross-continental seasonal risk) and explicit DeltaEO / rho audit (they compute no fairness metric).
- **Target section:** Section 2 Line B (prominent); Section 4 (VLA methods).

#### 3. Chen et al. 2025, GAL [B-agent-vlm] [baseline]
- **Key:** `chen2025gal` (arXiv:2510.12061, 2025-10-14)
- **Takeaway:** Geospatial Awareness Layer that grounds LLM agents in infrastructure, demographic, terrain, and weather data for wildfire response.
- **Relation to FireFair:** Direct conceptual competitor to our Equity Agent's geospatial grounding. Must be distinguished: GAL grounds descriptively; FireFair's Equity Agent produces explicit quantitative SVI-quartile DeltaEO and rho.
- **Target section:** Section 2 Line B; Section 4 (Equity Agent).

#### 4. Esparza et al. 2025, VLM Damage Assessment on 2025 LA Fires [B-agent-vlm] [baseline]
- **Key:** `esparza2025damagevlm` (arXiv:2509.01895, 2025-09-02 / v2 2026-04-04)
- **Takeaway:** Zero-shot MLLM pipeline for wildfire property damage classification on 2025 Eaton and Palisades fire ground-level imagery.
- **Relation to FireFair:** Same 2025 LA fires we reference in Section 1; same VLM-for-wildfire paradigm; different modality. Easy differentiation (ground-level vs. Sentinel-2).
- **Target section:** Section 2 Line B (optionally Section 1 next to the fire references).

### DISCUSS (4)

#### 1. Irvin et al. 2025, TEOChat (ICLR 2025) [B-agent-vlm] [baseline]
- **Key:** `irvin2025teochat` (arXiv:2410.06234 v2 2025-01-27)
- **Takeaway:** Temporal Earth-observation VLM trained on 554k examples; outperforms GPT-4o / Gemini 1.5 Pro on temporal EO reasoning.
- **Rationale:** Our Sentinel-2 VLA operates on temporal multi-image data; TEOChat is the ICLR-2025 baseline for that regime.
- **Recommendation:** **CITE-NOW.** One sentence in Line B as the temporal-EO VLM baseline.

#### 2. Danish et al. 2025, GEOBench-VLM (ICCV 2025) [B-agent-vlm] [benchmark]
- **Key:** `danish2025geobench` (arXiv:2411.19325)
- **Takeaway:** Even the best open VLM (LLaVa-OneVision) reaches ~42% MCQ on 31 geospatial tasks; GPT-4o barely competitive.
- **Rationale:** Quantitative motivation for multi-agent orchestration: a raw VLM call is insufficient for geospatial hazard reasoning.
- **Recommendation:** **CITE-NOW.** One sentence in Line B motivation. Pairs with SmokeBench for a one-two punch.

#### 3. Qi et al. 2026, SmokeBench (WACV 2026) [B-agent-vlm] [benchmark]
- **Key:** `qi2026smokebench` (arXiv:2512.11215)
- **Takeaway:** GPT-4o, Gemini-2.5-Pro, Qwen2.5-VL, InternVL3 all fail at early-stage wildfire smoke localization.
- **Rationale:** Same motivation logic as GEOBench-VLM, specialized to wildfire smoke. Strong defensive support for FireFair's Sentinel-2 VLA + agent-orchestration design.
- **Recommendation:** **CITE-NOW.** One sentence alongside GEOBench-VLM.

#### 4. Szwarcman et al. 2024, Prithvi-EO-2.0 [B-agent-vlm] [baseline]
- **Key:** `szwarcman2024prithvi` (arXiv:2412.02732)
- **Takeaway:** NASA/IBM multi-temporal foundation model on 4.2M HLS / Sentinel-2 time series; +8% over Prithvi-EO v1; open weights.
- **Rationale:** If FireFair's VLA is a generic VLM fine-tuned on wildfire imagery, a reviewer will ask "why not fine-tune from Prithvi?" Cite at least defensively.
- **Recommendation:** **CITE-NOW one sentence** in the VLA methods section if we touch the foundation-model-choice question; otherwise POST-SUBMIT. Very low cost.

### POST-SUBMIT (5)

- `soni2025earthdial` (CVPR 2025; arXiv:2412.15190) -- EarthDial multi-sensor EO dialogue assistant; 11M QA pairs across 44 tasks.
- `gao2025instructor` (IJAEOG 2025; arXiv:2503.00566) -- Instructor-Worker LLM for policy recommendation on the Jan 2025 LA fires; same CA / LA focus as our motivation section, different target (air-quality policy vs. ignition risk).
- `hyun2025crewwildfire` (arXiv:2507.05178) -- CREW-WILDFIRE procedural multi-agent wildfire benchmark; demonstrates current frameworks fail at coordination / spatial reasoning at scale.
- `liu2025detectiumfire` (NeurIPS 2025 D&B; arXiv:2511.02495) -- DetectiumFire multi-modal fire dataset (22.5k images + 2.5k videos).
- `forestfirevlm2025` (Drones MDPI 2025) -- ForestFireVLM-7B fine-tuned for UAV early wildfire detection; outperforms GPT-4o / Gemini.

### WATCH (1)

- `syed2025cloudburst` (arXiv:2511.22767) -- Non-wildfire agentic-AI cloudburst framework. Relevant only if Line B framing needs to establish that agentic-AI-for-hazard is a recognized emerging pattern.

### Line B Coverage Gaps (preliminary)

1. **No VLM-wildfire paper in our sweep computes any fairness or EJ metric.** FireScope, GAL, MARSHA, Esparza, EarthDial, Prithvi-EO-2.0, TEOChat, GEOBench-VLM, SmokeBench -- every Line B paper is either task-performance, benchmark, or RAG-decision-support. FireFair's Equity Agent is unchallenged in the VLM-wildfire neighbourhood and should be framed that way.
2. **No multi-agent wildfire system integrates a quantitative EJ audit.** MARSHA (4-agent decision-support), GAL (single LLM + structured geo grounding), CREW-WILDFIRE (benchmark, not model), Instructor-Worker (air-quality analysis). None compute DeltaEO or rho. This is an explicit positioning opportunity in Related Work.
3. **Sentinel-2 specifically is used by FireScope and Prithvi-EO-2.0 (via HLS).** Our Sentinel-2 VLA story therefore has two natural neighbours. Make the comparison explicit rather than leaving it implicit.
4. **No chain-of-thought-reasoning wildfire agent published before FireScope (Nov 2025).** This limits our ability to cite CoT-for-wildfire as a prior tradition; we may need to cite general-purpose CoT (Wei et al., 2022) and frame FireFair's Report Agent as a task-adapted application of that pattern.
5. **OpenReview / ICLR 2026 queries returned little wildfire-specific content.** This is expected (ICLR 2026 dates are Apr 23-27, so the window is still partly under review). Residual gap: we can't cite ICLR 2026 papers that may land in the intervening month. Recommend rerunning this search week-of 2026-05-01.

---

## Line C -- Environmental justice / spatial fairness

Lookback: 36 months (since 2023-04-17). Deepest sweep per your "Line C is weakest, bias effort accordingly" instruction.

Kept: **17 new papers** (plus 3 draft-promoted entries already in `candidates.bib`).

### CITE-NOW (5)

#### 1. Huynh et al. 2024, CalEnviroScreen audit [C-equity] [method]
- **Key:** `huynh2024mitigating` (Nat. Machine Intelligence 6:187-194, 2024; DOI:10.1038/s42256-024-00793-y)
- **Takeaway:** Full audit of CalEnviroScreen (a policy EJ data tool); shows parameter-sensitivity has \$2.08B funding consequence.
- **Relation to FireFair:** Nearest peer-reviewed methodological analog to our DeltaEO / rho audit; the closest precedent for "apply an EJ-audit lens to a deployed algorithmic EJ instrument." A fairness-aware reviewer will ask why we did not benchmark against an allocative-sensitivity analysis; citing Huynh signals we know the literature.
- **Target section:** Section 2 Line C; Section 5 (Equity metrics).

#### 2. Saxena et al. 2024, Spatial Fairness [C-equity] [method]
- **Key:** `saxena2024spatial` (arXiv:2403.14040)
- **Takeaway:** Position paper arguing spatial fairness is under-defined; catalogues failure modes of existing spatial-fairness methods.
- **Relation to FireFair:** Directly challenges DeltaEO / rho. Citing defensively pre-empts the strongest reviewer critique: "your fairness metric does not provably reduce discrimination on protected attributes."
- **Target section:** Section 5 (metric definitions); Limitations.

#### 3. Vargo et al. 2023, SVI + Wildfire Smoke [C-equity]
- **Key:** `vargo2023social` (AJPH 113(7):759-767, 2023; DOI:10.2105/AJPH.2023.307286)
- **Takeaway:** 2011-2021 US-wide analysis showing heavy-smoke person-day increases concentrated in minority / limited-English / low-education communities.
- **Relation to FireFair:** Canonical SVI-and-wildfire-smoke reference; omitting it signals unfamiliarity. Pairs with `dennin2025smokejustice` and `modaresirad2023social` as our three-pillar equity motivation.
- **Target section:** Section 2 Line C (equity motivation paragraph).

#### 4. Pollack et al. 2024, Flood-risk Equity Measurements [C-equity] [method]
- **Key:** `pollack2024flood` (Nat. Sustainability 7:823-832, 2024; DOI:10.1038/s41893-024-01345-3)
- **Takeaway:** Survey-style Nature Sustainability paper on how "equity" is operationalized in flood-risk peer-reviewed work; flags that most studies fail to defend their value judgements.
- **Relation to FireFair:** Cross-hazard methodological precedent. Citing Pollack lets us position DeltaEO / rho within a broader, recognized hazard-equity measurement tradition rather than as a wildfire-specific ad hoc metric.
- **Target section:** Section 2 Line C; Section 5.

#### 5. Barocas, Hardt, Narayanan 2023, FairML textbook [C-equity] [method]
- **Key:** `barocas2023fairml` (MIT Press, 2023)
- **Takeaway:** Foundational FairML textbook; Chapter 3 covers equal-opportunity / equalized-odds from Hardt/Price/Srebro 2016, which is DeltaEO's direct origin.
- **Relation to FireFair:** Single citation at DeltaEO equation; signals AIES / FAccT-aware framing. Zero narrative cost.
- **Target section:** Section 5 (DeltaEO equation footnote).

### DISCUSS (4)

#### 1. Salazar-Miranda et al. 2024, Redlining and Climate Risk [C-equity]
- **Key:** `salazarmiranda2024redlining` (Nature Cities 1:436-444, 2024; DOI:10.1038/s44284-024-00076-y)
- **Takeaway:** Boundary-design analysis of 202 US cities showing HOLC-D "redlined" areas face disproportionate flood + extreme-heat risk, mediated by reduced tree canopy and foundation height.
- **Rationale:** Powerful framing asset -- if FireFair wants to position its EJ audit as connecting present-day ML predictions to historical structural-racism patterns.
- **Recommendation:** **CITE-NOW in Section 1 or Section 2 Line C** if we adopt this framing; otherwise POST-SUBMIT. One sentence either way.

#### 2. Letellier et al. 2025, GRF on CA Wildfire Smoke Vulnerability [C-equity]
- **Key:** `letellier2025grf` (Environment International 2025; DOI:10.1016/j.envint.2025.109955)
- **Takeaway:** Generalized random forest on CA hospital admissions 2006-2019; under-75 and Black/Other race+ethnicity groups have highest wildfire-smoke mortality risk.
- **Rationale:** Closest 2025 CA+ML+health-vulnerability peer. Supports our SVI-quartile analysis with a concrete downstream health-outcomes link.
- **Recommendation:** **CITE-NOW in Line C, one sentence.** Low cost.

#### 3. Cai & Balestriero 2025, FAIR-Earth [C-equity] [dataset] [method]
- **Key:** `cai2025fairearth` (arXiv:2502.06831)
- **Takeaway:** FAIR-Earth dataset + spherical wavelet encodings to audit fairness of implicit neural representations of Earth data; high-frequency regions (islands, coastlines) are under-modeled.
- **Rationale:** Orthogonal to DeltaEO / rho (audits *representation* not *prediction*), but a reviewer might ask whether we audited the representation layer of our Sentinel-2 VLA.
- **Recommendation:** DISCUSS -> lean POST-SUBMIT. One defensive sentence in Limitations if space allows ("representation-level fairness audits are out of scope; see Cai & Balestriero 2025"); otherwise safe to skip.

#### 4. Ghamisi et al. 2024, Responsible AI for EO [C-equity]
- **Key:** `ghamisi2024responsibleai` (IEEE GRSM 2025, accepted; arXiv:2405.20868)
- **Takeaway:** Broad responsible-AI-for-EO survey; covers fairness, privacy, security, scientific excellence.
- **Rationale:** Useful only if FireFair invokes a "responsible AI for EO" framing explicitly.
- **Recommendation:** DISCUSS -> lean POST-SUBMIT. Low cost to add one sentence, but also low cost to skip.

### POST-SUBMIT (7)

Grouped by sub-theme; one-liner each.

*Descriptive epidemiology (non-ML) -- useful background, not direct baselines.*
- `schwarz2025mortality` (PNAS 2025) -- Kaiser Permanente SoCal cohort 2009-2019; subpopulation heterogeneity in long-term wildfire-smoke mortality.
- `nguyen2025pm25disparity` (ACS ES&T Air 2025; author TODO) -- Wildland fire smoke further widens baseline PM2.5 disparities for Black / AI/AN / non-urban populations.
- `jung2024chvi` (STOTEN 906:167834, 2024) -- CONUS Community Health Vulnerability Index for wildland fire smoke.
- `jonesngo2025compound` (Earth's Future 2025; authors/volume TODO) -- Compound wildfire-smoke + extreme-heat exposure in CA 2011-2020.

*Descriptive SVI + wildfire.*
- `schumann2024svi` (Natural Hazards 120:4297-4327, 2024) -- Geography of SVI and wildfire occurrence 1984-2018 across conterminous US.
- `xie2024minorities` (IJDRR 114:104949, 2024) -- Getis-Ord Gi* + Location Amplitude Index on CA minority wildfire vulnerability.

*Datasets and adjacent methods.*
- `pourmohamad2024essd` (Earth System Science Data 16:3045, 2024) -- FPA FOD-Attributes adds 270 attributes including SVI / EJ metrics to the USFS FPA FOD database. Potential covariate source if FireFair expands to CONUS.
- `shaham2023fairspatial` (arXiv:2302.02306, 2023) -- Fair Spatial Indexing: a spatial-data-structures approach to group spatial fairness. Relevant only if we move toward spatial-index-level mitigation (e.g., a journal extension).

### WATCH (1)

- `franchi2023algorithms` (FAccT 2023) -- "Algorithms as Social-Ecological-Technological Systems: An EJ Lens on Algorithmic Audits." Useful if we frame Discussion as situating FireFair in a FAccT-style audit tradition. Older than the 36-month window by a few months -- retain as a signal of where AIES/FAccT-audience framing should anchor.

### Line C Coverage Gaps (consolidated below)

---

## Consolidated Coverage Gaps

**This is the section that matters most for reviewer-pushback risk. Read it before writing the Limitations section.**

### 1. No prior wildfire-prediction ML model audits itself with equal-opportunity or per-capita disparate-exposure

Every EJ-wildfire paper found in this sweep is either descriptive epidemiology (Vargo, Modaresi Rad, Dennin, Jung, Schwarz, Jones-Ngo, Letellier) *using SVI / CES as a covariate or stratifier*, or an audit of a policy EJ data tool (Huynh). **None applies DeltaEO or a per-capita exposure ratio as a fairness constraint on an ignition- or risk-prediction ML model.** FireFair is, as far as this sweep shows, the first. That is simultaneously our contribution and our largest reviewer-pushback vulnerability.

- **Mitigation:** (a) cite `saxena2024spatial` as the closest conceptual predecessor and explicitly flag the gap; (b) cite `huynh2024mitigating` as the analog audit of an EJ-policy system; (c) cite `pollack2024flood` as the cross-hazard methodological precedent in flood risk; (d) cite `barocas2023fairml` for the equal-opportunity derivation. Together these four citations form a defensible "related-yet-distinct" lineage for DeltaEO / rho.

### 2. Spatial-fairness literature is theoretical / positional, not empirical on hazard data

`saxena2024spatial` and `shaham2023fairspatial` both argue for the importance of spatial fairness without demonstrating it on hazard data. `cai2025fairearth` demonstrates fairness for *Earth representations* but not for hazard prediction. There is no published SOTA comparator for rho (per-capita alert exposure ratio) in wildfire or any other hazard ML context.

- **Risk:** Reviewers may claim rho is ad hoc.
- **Mitigation:** frame rho against the 80%-rule / disparate-impact tradition (EEOC Uniform Guidelines) rather than against a wildfire-specific prior; one explicit sentence locating it in the civil-rights-compliance lineage goes a long way.

### 3. FAccT / AIES / EAAMO have minimal wildfire-specific content

The 2024 and 2025 FAccT/AIES programs surface no directly-on-point wildfire fairness papers. Closest is `franchi2023algorithms` (2023 FAccT, EJ lens for algorithmic audits). Wildfire-equity work lives in AJPH / CommsEarth&Env / Science Advances / Nat. Sustainability, not the ML-fairness venues. **That cultural gap is itself a finding: FireFair is one of very few works bridging hazard-prediction ML with the ML-fairness community.**

- **Risk:** AIES / FAccT-style reviewers may expect a stronger theoretical fairness contribution.
- **Mitigation:** explicitly cite the textbook (`barocas2023fairml`) and position FireFair as an applied contribution to a policy-relevant hazard-prediction problem, not a fairness-theory contribution.

### 4. No VLM-for-wildfire paper in our sweep computes any fairness / EJ metric

FireScope, GAL, MARSHA, Esparza, EarthDial, Prithvi-EO-2.0, TEOChat, GEOBench-VLM, SmokeBench -- every Line B paper is task-performance, benchmark, or RAG-decision-support. FireFair's Equity Agent is unchallenged in the VLM-wildfire neighbourhood.

- **Positioning opportunity:** One sentence in Section 2 Line B stating this gap sells the Equity Agent's novelty more effectively than any architectural detail.

### 5. InceptionTime + CutMix backbone has no 2025 wildfire external validation

2025 TSC competitors are moving to Mamba (TSCMamba, ms-Mamba) and ViT variants. CutMix-for-fire-time-series is unpublished.

- **Risk:** Reviewer may ask "why not Mamba?"
- **Mitigation:** One-sentence justification (parameter efficiency, InceptionTime's strong TSC track record on low- to mid-dimensional tabular TS, fit to CA daily-meteorology dimensionality). Cheap defensive insurance.

### 6. Most 2025 CA-specific wildfire ML targets spread, damage, or containment -- not ignition

Jia & Opabola (damage), Zhou & Cheng (spread), Zheng & Cheng (spread + firebreaks), Bhardwaj (containment). **CAWFI (`bhowmik2025cawfi`) is the only CA-wide ignition-adjacent 2025 dataset**; omitting it is the single biggest reviewer-pushback risk on Line A.

### 7. ICLR 2026 has not yet surfaced a useful wildfire hit

Conference dates are 2026-04-23 to 04-27, so the discussion papers will post in the weeks after this sweep. Rerun this query week-of 2026-05-01 for any late catches before the GoodIT submission on 2026-05-17.

---

## Bottom line

- **12 CITE-NOW** across all three lines, but only ~7 of those are "mandatory" (the reviewer-will-ask-about ones): `bhowmik2025cawfi`, `michail2026firecastnet`, `xie2025marsha`, `markov2025firescope`, `huynh2024mitigating`, `saxena2024spatial`, `vargo2023social`. The remaining 5 are "should add, one sentence each."
- **1 action I would take even if no other changes are made:** write the defensive paragraph in Limitations that acknowledges FireFair is the first wildfire-prediction ML model audited with equal-opportunity and per-capita-exposure metrics, and cite `saxena2024spatial` + `huynh2024mitigating` + `pollack2024flood` as the closest adjacent traditions. One paragraph preempts the majority of fairness-reviewer questions.
- **Do not try to add every DISCUSS item.** The 5 Line A DISCUSS-lean-CITE-NOW items (TEOChat, GEOBench-VLM, SmokeBench, Salazar-Miranda, Letellier) are all single-sentence additions that share the same framing beat, so they can go in together (~45 min of prose).
