# What the mining already established

These are findings, not proposals. Each was produced by querying public data or primary
literature during this analysis. They matter because they change what the proposal should
say — several of them before any new analysis is run at all.

Status markers: **[V]** verified from the primary source · **[V-]** verified with a
correction/caveat · **[U]** unverified from this environment, confirm before use.

---

## 1. The L1CAM problem is worse than "a controversy"

The proposal's Aim 1 rests on L1CAM (CD171) immunocapture enriching neuron-derived vesicles.
Four independent lines now say the captured L1CAM is largely **not vesicle-borne**:

- **[V] Size-exclusion chromatography of human CSF, 5,416 proteins by Olink Explore HT**
  (Norman et al., *J Extracell Vesicles* 2025, PMC11913887; data + code, GPL-3.0, at
  `github.com/Walt-Lab/ev_association_olink_analysis`). Re-analysing the deposited NPX matrix
  against the plate map: CD63 (EV positive control) peaks in the early EV fractions and
  declines, while **L1CAM rises monotonically into the late, soluble-protein fractions**
  (F9 −5.06 → F13 +2.44). NCAM1, CNTN2, CHL1, SNAP25 and GAP43 behave the same way. None of
  L1CAM, NCAM1, ATP1A3, SNAP25, GAP43, CNTN2, SLC1A3 or GFAP appears among the proteins
  meeting the paper's EV-fractionation criteria.
  - **[V-]** Two caveats on our own re-analysis: the paper's methods use only fractions
    7, 9, 10, 11, 12, 13 for the EV call, so per-fraction values quoted outside that set need
    re-checking; and the paper's text says the pipeline identifies **57** unique transmembrane
    and internal EV-associated proteins, so the "295 proteins" figure must be re-derived from
    the repo before it is cited.

- **[V] Independent German replication using the identical antibody clone.** Kadam et al.,
  *Mol Neurobiol* 2025 (PMID 40210837, PMC12289729; PRIDE **PXD058777**), Tübingen/Ulm/DZNE.
  Using biotinylated anti-L1CAM clone **eBio5G3 (13-1719-82)** — the same clone as Kapogiannis
  — L1CAM immunoprecipitation of the SEC EV fraction yielded **no L1CAM enrichment**; L1CAM was
  recovered from the EV-*depleted* protein fraction. NTA size distributions for the L1CAM-IP
  and the anti-calnexin control IP were superimposable across 8 independent experiments.
  Constructively: **NfL was detected in both CSF- and blood-derived EVs**, so neuronal EVs are
  there — they are just not L1CAM-enriched.

- **[V] Peptide topology in the deepest public plasma EV proteome.** Mag-Net (PXD042947;
  `github.com/uw-maccosslab/manuscript-mag-net`, Zenodo **10.5281/zenodo.15273142**): all
  **4/4 detected L1CAM peptides and all 13/13 NCAM1 peptides map to extracellular domains**,
  with zero transmembrane or cytoplasmic peptides — the mass-spectrometric signature of a shed
  ectodomain. The same pattern was reported independently in CSF, where ATP1A3 and NCAM1 *did*
  yield cytoplasmic peptides.

- **[V-] Both capture clones fail on a defined source.** Collier 2025 reports that **both**
  anti-L1CAM clones in use (5G3 *and* UJ127) failed to immunocapture CD81-positive SH-SY5Y EVs.

**[V-] One mechanistic story does not hold.** Reimann et al., *J Extracell Biol* 2026
(PMID 42006582) confirms ADAM10 is catalytically active on small EVs and lists L1CAM among
known substrates present — but explicitly reports that L1CAM, NOTCH1, APP, N-cadherin and
NCAM1 were **not** affected by sEV-ADAM10 inhibition (only PCDHGC3 was). Vesicle-borne ADAM10
shedding of L1CAM is a hypothesis to test, not a finding to assert.

**[V] The founding papers' reporting quality is on the public record.** EV-TRACK scores the
Kapogiannis 2015 study (record **EV140348**) at **EV-METRIC 2.0 = 19.44%, with a
particle-characterisation subscore of 0**. Mustapic 2017, the canonical protocol paper
(EV170062), scores 58.55%. An independent audit of 51 L1CAM-EV papers found 19 reported no
physical characterisation at all, and only 10 showed a depleted non-EV marker.

**[V] The capture reagent has no independent validation.** Clone 5G3 does not appear in the
YCharOS knockout-validated antibody corpus. Norman 2021 additionally showed the anti-L1CAM
antibody binds recombinant α-synuclein ~3-fold above IgG.

> **What follows for the proposal.** This is survivable, and handling it well is the single
> biggest opportunity in the document. It requires: a named negative-capture arm (isotype or
> anti-calnexin, processed identically at every input volume — no cited paper has one); a
> proteinase-K protection assay as an explicit pre-registered go/no-go; and a second capture
> antigen run head-to-head. It also argues for retitling Aim 1 from *"establish L1CAM
> immunocapture"* to *"benchmark neuronal EV capture antigens"*, which is publishable
> whichever way the result falls.

---

## 2. ATP1A3 beats L1CAM on brain specificity by three orders of magnitude

**[V] GTEx v10 median TPM** (public GCS bucket, no registration):

| Gene | Hypothalamus | Cortex | Tibial nerve | Subcut. adipose | Whole blood |
| --- | --- | --- | --- | --- | --- |
| **ATP1A3** | 227.7 | 250.1 | 0.17 | 0.14 | 1.17 |
| **L1CAM** | 48.3 | 70.5 | **113.0** | — | — |
| **NEFL** | 143.8 | — | — | 0.08 | 0.25 |
| **SNAP25** | 93.9 | — | — | 0.46 | 0.05 |
| **IRS1** | **1.92** | — | — | **10.63** | — |
| **IRS2** | **16.53** | — | — | — | — |

Two things jump out. **L1CAM is higher in peripheral nerve than in hypothalamus** — a
brain:periphery margin of 0.43×, against ATP1A3's >1,000×. In a cohort stratified on
peripheral insulin resistance, where diabetic peripheral neuropathy tracks the same
stratifier, peripheral-nerve EVs are a competing explanation for exactly the signal Aim 2 is
hunting. No one in the nEV field states this; stating it first is a genuine contribution, and
it argues for a Schwann-cell counter-marker (PMP22 or MPZ) on the surface panel.

Second, **IRS1 is not the dominant brain isoform.** Hypothalamic IRS1 is 8.6× lower than IRS2
and 5.5× lower than IRS1 in subcutaneous adipose.

**[V] The GLAST arm does not survive scrutiny.** SLC1A3 has only a ~3.7× brain:adipose margin
(17.5–18.1 TPM in adipose), is detected in 73.7% of brain myeloid cells (vs 91.9% of
astrocytes), does not appear among the EV-fractionating proteins in the Norman dataset, and is
not on any Olink panel. In an obesity cohort a GLAST arm risks profiling adipose-tissue-
macrophage EVs and calling them astrocytic. GFAP or ALDH1L1 is the better glial marker.

---

## 3. The novelty claim is refuted, and the primary endpoint has already returned nulls

The proposal states *"nEVs have not been measured in human obesity."* As literally worded this
is false, and the counter-evidence is one PubMed query away:

- **[V] McIntyre 2025** (*Sci Rep*, PMC12216818) — **n = 71**, BMI 35.6, same 5G3 clone, same
  three ELISA kits. The pSer312/pan-Tyr IRS-1 ratio **R** against HOMA2-IR:
  **r = −0.036, p = 0.768.** No association with any cognitive or network outcome.
  SD(R) = 4.23 on a mean of 6.67 — a 63% between-subject CV.
- **[V] Manolopoulos 2025** (*Ann Clin Transl Neurol*, PMID 40665589) — **1,130 plasma
  samples from 676 WHIMS/LLS women**, L1CAM immunocapture. Verbatim: *"No group differences
  were found for Aβ42, Tau proteins, or pS312-IRS-1."* A second, independent, large null on
  the exact proposed primary analyte.
- **[V] Evers 2025** (*Psychoneuroendocrinology*, PMID 40992133) — **n = 125** cognitively
  intact adults, 3-year follow-up, peripheral IR by **steady-state plasma glucose during the
  insulin-suppression test** (better than HOMA-IR), central IR by p-IRS1 in plasma nEVs. This
  is a larger, better-phenotyped, already-published version of the divergence hypothesis. It
  reports p-IRS1 correlating **inversely** with SSPG, BMI and leptin.
- **[V] Kapogiannis 2024** (*Cell Metab*, PMC11305918) — n = 40 at BMI 34.4 with HOMA2-IR
  measured, i.e. nEVs in obesity, from the founding lab itself.
- **[V]** The 2015 paper the proposal cites as its foundation already contains a
  cognitively-normal **type 2 diabetes** arm.

**[V-] A citation error compounds this.** "Cleary 2024 Alz&Dem" is a 2025 *review*
(*Alzheimers Dement* 2025;21:e14497), not a primary case-control replication. That same review
states that whether nEV IRS-1 measures correlate with post-mortem assays of brain insulin
signalling *"remains to be determined."*

> **What follows.** The claim has to be narrowed to what survives: no nEV study in a
> **matched-BMI insulin-sensitive vs insulin-resistant obesity-subtype design**, none in a
> **European bariatric biobank**, none in **serum**, and none with **peripheral–central
> discordance as the pre-specified primary endpoint**. Cite McIntyre and Manolopoulos in the
> same paragraph. Finding these independently is far worse for a reviewer than being told.

---

## 4. The panel measures the analytes with the weakest published link to insulin resistance

**[V]** In two independent obesity cohorts, nEV **Akt, pAkt-Ser473 and pERK1/2** track
HOMA-IR — and the IRS-1 phospho-forms do not:

| Study | n | Finding |
| --- | --- | --- |
| Kapogiannis 2024 *Cell Metab* (PMC11305918) | 40, BMI 34.4 | Δ HOMA2-IR vs nEV Akt ρ = −0.46; pS473-Akt ρ = −0.46; pERK1/2 ρ = −0.51. **Not** IRS-1 phospho-forms. |
| Malin 2025 *Aging Cell* (PMC11709104) **[V-]** | 21 (randomised two-arm exercise trial, not single-arm) | total Akt vs HOMA-IR r = −0.48; pAkt-S473 vs insulin sensitivity r = −0.49 to −0.53 |

These analytes are essentially free on the same MSD or MILLIPLEX Akt/mTOR multiplex.

**[V] Site choice is also dated.** The human brain-tissue evidence for brain insulin
resistance (Talbot 2012 *JCI*) implicates **Ser616 and Ser636/639**, not Ser312. Ser312 is
defensible — the Religious Orders Study post-mortem series found it was the only site
differing by diabetes — but that defence has to be written.

**[V] The pTyr arm is missing.** Aim 2 lists total IRS-1, pSer312, GFAP and IL-6. The
published discriminator the whole proposal rests on is the **ratio pSer312/pan-Tyr**. As
written, the study cannot compute its own headline endpoint.

**[V] Nomenclature hazard.** Human IRS1 (P35568) has **both** a Ser307 and a Ser312, targeted
by different kinases. Human Ser312 = mouse Ser307; human Ser307 = mouse Ser302. Any figure
legend reading "pSer307" without a species is wrong.

---

## 5. n = 24/group is not powered for any credible prior

**[V]** The available priors, ordered by credibility:

| Source | Effect | Comment |
| --- | --- | --- |
| Religious Orders Study, n = 150 autopsied (PMC11346412) | **d ≈ 0.40** | The applicant's exact analyte (rodent pS307 = human Ser312) measured in *actual human brain*, diabetes vs none. Mean difference 0.05 (95% CI 0.01–0.09). |
| MHO vs MUO meta-analysis, 91 studies, 435,007 individuals | **&#124;SMD&#124; ≈ 0.43** | CRP — the best-characterised circulating marker in exactly this contrast |
| Kapogiannis 2015, reconstructed | d ≈ 4.0 | **Not a prior — a warning.** The paper reports **SEM, not SD**; mistaking one for the other inflates every effect size by √n (≈4.5–5× here). |

**[V]** Against these, at n = 24/group, α = 0.05, two-sided: minimum detectable **d = 0.81**,
rising to **0.96–0.99** under Bonferroni across 4–5 analytes. Power is 79% at d = 0.80,
**32% at d = 0.43**, 6% at d = 0.10. Using McIntyre's obese-cohort SD(R) = 4.23, the minimum
detectable difference in R is 3.4 units — a >50% shift in group mean.

**[V] The divergence hunt is unfalsifiable as written.** No discordance rule is given. At
N = 48 total the minimum detectable |r| is **0.395**. The best measured brain–periphery
coupling in humans (Kullmann 2023, *Diabetes Obes Metab*, PMID 37046367, n ≈ 110, intranasal
insulin + fMRI CBF) is **β ≈ −0.19 in a single region (amygdala, p = .023)** — about 3.6% of
variance. So roughly half the sample will be "discordant" by construction. The endpoint needs
a pre-registered residual threshold simulated against an **r ≈ 0.19 null, not an r = 0 null**.

> That Kullmann result cuts both ways, and belongs in the introduction: it is simultaneously
> the **best published empirical support for the divergence premise** — brain and peripheral
> insulin action are largely decoupled in humans, measured directly at n ≈ 110 — and the
> reason the proposed n cannot detect the decoupling.

---

## 6. The assay plan may not be purchasable as written

- **[V] No Simoa assay for IRS-1 or phospho-Ser312-IRS-1 could be found** in the Quanterix
  catalogue. Every published nEV IRS-1 measurement used plate ELISA, Western blot, MSD or
  Luminex. "By Simoa or MSD" in a funded budget is a deliverability risk.
- **[V] The reference reagent has no absolute standard.** Invitrogen KHO0521 reports
  **arbitrary U/mL**, and is validated for cell lysates only — serum and plasma are not listed
  matrices. Effect sizes in lot-dependent arbitrary units do not transfer to a follow-on study
  or to DIRECT-PLUS. Budget single-lot procurement for the whole study, plus spike-recovery
  and dilutional linearity in an EV lysate matrix.
- **[V] Free-plasma GFAP is the wrong endpoint.** In SOL-INCA (n = 6,264, Simoa HD-X), log
  GFAP for diabetes vs no diabetes was **β = 0.025 (95% CI −0.020 to 0.070, p = 0.276)** —
  null at n > 6,000 — while log NfL was β = 0.253 (0.197–0.309, p < 0.001). GFAP additionally
  carries a **blood-volume dilution confound** in exactly this population, and both GFAP and
  NfL are *lower* in obesity and rise after bariatric weight loss. At n = 24/group there is
  roughly 6% power for the GFAP effect.
  - Keeping GFAP as *EV-associated cargo* is defensible, and the argument that
    vesicle-normalised readouts should be immune to the dilution artefact is a genuine
    argument **for** the approach — worth making explicitly.
- **[V] A missing control invalidates Aim 1.** Kadam used anti-calnexin; Nogueras-Ortiz used
  isotype IgG. Without a matched negative-capture arm processed identically at every input
  volume, no Aim 1 result is interpretable. A **biotin-blocking or depletion step** is also
  unspecified, despite a biotinylated capture antibody feeding streptavidin-based detection —
  a documented failure mode that can manufacture a spurious group difference.

---

## 7. Serum vs plasma is an unresolved internal inconsistency

**[V]** Aim 1 says *serum*; the September work programme says *plasma*. Every published
L1CAM-nEV IRS-1 dataset (Kapogiannis, McIntyre, Delgado-Peraza, Malin, Nogueras-Ortiz) is
**plasma**. Serum means 30–60 minutes of room-temperature clotting — the worst possible
pre-analytical window when the primary analyte is a phospho-epitope — plus platelet EV release
into a population that overlaps the target vesicles in size and density. MISEV2023 permits
serum but requires quantified platelet and haemolysis burden.

---

## 8. The applicant's own data already answers a mechanistic-plausibility question

**[V]** Re-analysis of **GSE137626** (Jais et al., *Neuron* 2020 — PNOC neuron BacTRAP
ribosome profiling, chow and HFD, public since 2020):

- EV biogenesis machinery is **enriched** in the PNOC IP: *Tsg101* +0.58 (chow), +0.69 (HFD);
  *Rab27b* enriched on HFD.
- *Irs2* enriched, *Insr* depleted — consistent with the GTEx picture that IRS2, not IRS1, is
  the dominant hypothalamic isoform.
- *Vamp2* +0.72 and *Gap43* +0.48 are enriched — **exactly the two single-EV neuronal
  validators used by Nogueras-Ortiz 2024**, a ready-made coherence argument.
- **[V-] A free panel correction:** *Cd9* is strongly depleted (−4.44). But note the
  correction — *Cd63* is **also** significantly depleted (−1.204 chow, −1.306 HFD, both
  q = 3.79e-4) and *Cd81* is only mildly depleted on HFD (−0.333, q = 0.031). The defensible
  statement is that **CD81 is closest to neutral and should be the primary tetraspanin**, with
  CD9-low reported as an expected biological signature rather than an isolation failure — not
  the stronger "use CD81 and CD63" claim.

This is hours of work on already-published in-house data, and it belongs in Preliminary Data.

---

## 9. Competition is real and closer than the proposal implies

- **[V] DPPOS / NIA (Kapogiannis, Mustapic)** hold nEV insulin-signalling data on **456
  prediabetes/T2D participants** at Year 22, inside a 1,654-participant ~23-year longitudinal
  cohort, with a stated intention to deposit. This is a genuine scoop risk and should be
  positioned against explicitly rather than ignored.
- **[V] Malin (Rutgers)** has already linked nEV cargo to *directly measured brain insulin
  action*: in n ≈ 15 adults (BMI ~31.8, HbA1c ~5.8%), L1CAM+GAP43+Neuroligin-3-captured nEV
  **pIR-Tyr1162/1163 correlated with left hippocampal CBF r = 0.51 (p = 0.05) and pallidum CBF
  r = 0.57 (p = 0.02)** after intranasal insulin with pCASL (*Compr Physiol* 2026, PMC13013089;
  *Exp Physiol* 2026, PMID 41439617). This is simultaneously the **strongest existing support
  for the entire proposal** — stronger than anything the proposal itself cites — and proof the
  applicant is not first. It must be cited, and it is the obvious collaboration.
- **[V] Chami 2025** (*Nat Med*, PMID 40940440, open at PMC12618246) already ran **2,920 Olink
  plasma proteins × 30,271 UKB participants against eight genetic obesity subtypes**. Any
  "obesity subtype × plasma proteome" analysis must be positioned against this.

---

## 10. The gap nobody has filled — and the applicant is uniquely placed to

**[V]** No published work has validated that nEV IRS-1 phosphorylation reflects brain insulin
signalling against any brain-tissue gold standard, **in any species**. The review the proposal
cites says so itself. The strongest human genetic evidence on IRS1 (Kilpeläinen 2011) places
the causal signal in **adipose, explicitly not brain**.

The applicant runs hypothalamic-neuron mouse models. **Plasma nEV cargo versus directly
measured hypothalamic insulin signalling in the same animal, ± HFD**, is the validation the
entire field lacks, is startable within four months, and would be the highest-impact output
available here. It is the one thing in this whole analysis that no public dataset can
substitute for — and the proposal does not currently use the applicant's in vivo capability
at all.
