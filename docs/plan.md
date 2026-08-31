# The plan

Two constraints shape everything below.

**Capacity.** A four-month, €24,550 wet-lab pilot supports roughly **25–35 person-days** of
in-silico work — about one day a week of the applicant's time plus, at best, half an analyst
for six weeks. The scouting behind this document surfaced ~80 candidate analyses totalling
well over 200 person-days. Most of it has to be killed, and it is killed explicitly in
[§6](#6-kill-list).

**Framing.** The failure mode to avoid is not "too much dry lab" — it is **fallback framing**.
If the proposal says anywhere *"if Aim 1 fails, we will pursue in-silico analyses,"* a reviewer
learns two things: the applicant does not believe Aim 1 will work, and bench money is being
hedged into laptop time. A Mini Flex fund exists to buy feasibility data.

> **The correct framing is de-risking preamble plus future directions, with nothing in
> between.** The specificity table, the topology audit and the PNOC re-analysis go into
> *Preliminary Data / Rationale* as **already-completed work** — a figure and half a page,
> demonstrating the applicant knows this literature better than the reviewer does. The
> recalibrated power analysis goes into *Methods/Statistics*. Everything else goes into
> *Future Directions* in three sentences. Nothing in the work programme, nothing in the Gantt
> chart, nothing in the budget.

---

## 1. Decisions to make before money is spent

The binding window is not "September" — it is the last moment before irreversible spend:
before the capture antibody is ordered, before assay kits are lot-reserved, and before a
single LOBB aliquot is thawed. Six decisions belong in that window. All are answerable from
evidence already assembled in [`audit.md`](audit.md); none needs new computation.

| # | Decision | Recommendation | Why |
| --- | --- | --- | --- |
| **D1** | Capture antigen | **Order an ATP1A3 antibody alongside 5G3 and run them head-to-head.** Retitle Aim 1 to *"benchmark neuronal EV capture antigens in serum."* | GTEx brain:periphery margin >1,000× vs L1CAM's 0.43×; ATP1A3 detected in 48/48 Mag-Net plasma EV samples; one published IP recovered 318 proteins vs 131 for L1CAM. Marginal cost is one antibody and one bead arm; the cost of *not* doing it is that a negative L1CAM result yields nothing publishable. |
| **D2** | Serum or plasma | **Audit the LOBB inventory this week** (tube type, time-to-spin, freeze-thaw count, matched aliquots). If matched EDTA plasma exists for ≥60% of candidates, switch primary matrix to plasma and keep serum as a bridging arm in ~8 donors. | Aim 1 says serum, the work programme says plasma, and every published prior is plasma. This is an internal database query, not public data, and it gates sample selection. |
| **D3** | Antibody clone | **5G3, biotinylated, eBioscience 13-1719-82 — and state the catalogue number in the proposal.** | Exactly the clone used by both Kapogiannis and the Kadam replication, so the result is directly comparable to both camps. 25 of 35 published capture papers gave no catalogue number. |
| **D4** | Platform and panel | **Call Quanterix and MSD/Merck to confirm what exists.** Expect the answer to convert "Simoa or MSD" into "MSD or MILLIPLEX Akt/mTOR 11-plex" — then **add pAkt-Ser473, total Akt and pERK1/2 as co-primary analytes.** | No Simoa assay for IRS-1 could be found. The 11-plex already carries pIR, pIRS-1-Ser636, pAkt-S473, total Akt, pERK1/2. The current panel measures the analytes with the *weakest* published link to insulin resistance and omits the three strongest. |
| **D5** | Phospho-sites | **Add pan-Tyr (non-negotiable) and Ser616.** Document human vs mouse numbering explicitly. | Without pan-Tyr the study cannot compute the ratio *R* its own rationale rests on. Ser616 anchors to the human brain-tissue literature (Talbot 2012). Both are nearly free on a multiplex. |
| **D6** | GFAP | **Drop free-plasma GFAP; substitute NfL.** Keep GFAP only as EV-associated cargo, with the dilution-immunity argument made explicitly. Pre-specify estimated blood volume (Nadler or Lemmens) as a covariate. | Free-plasma GFAP is null for diabetes at n = 6,264 and inversely confounded by blood volume and BMI; ~6% power at n = 24/group. |

Alongside these, three things cost an email each and should go out immediately: the **LOBB
inventory audit**; **Hoffmann/Blüher** on whether the existing Helmholtz UK Biobank
application's scope covers proteomics; and **Kapogiannis/Mustapic (DPPOS)** and **Malin
(Rutgers)** on collaboration. A refusal costs nothing.

---

## 2. Tier A — startable now, fully open, no registration

Ranked by value per person-day. A1–A3 are the ones that will actually get done and that belong
in the proposal as preliminary data.

### A1 · Peptide-topology and detectability audit — *3–4 days*
**Question.** Is the L1CAM you will capture membrane-anchored, and are the Aim 2 analytes
reachable by any method other than immunoassay?
**Data.** PXD042947 via `github.com/uw-maccosslab/manuscript-mag-net` (Zenodo
10.5281/zenodo.15273142) — released Skyline matrices, plus per-protein LOD/LOQ. Clone with
`GIT_LFS_SKIP_SMUDGE=1`; ~2.4 GB.
**Method.** Python/pandas. Join peptides to UniProt REST topological features (L1CAM P32004:
signal 1–19, extracellular 20–1120, TM 1121–1143, cytoplasmic 1144–1257) by interval-join on
peptide start/end. Positive controls ATP1A3, GRIA2, tetraspanins (cytoplasmic peptides *should*
be recoverable); negative controls ALB, APOB.
**Endpoint.** Detected peptides in cytoplasmic vs extracellular domains per candidate antigen,
per biofluid; binary "membrane-anchored evidence present/absent."
**Decision rule.** Already largely answered (4/4 L1CAM and 13/13 NCAM1 peptides extracellular;
IRS1 and INSR absent from both matrices). Two consequences go straight into the text: **the
immunoassay route is mandatory, not preferential** — which converts a budget line into a
justified choice — and **the proteinase-K protection assay becomes a named Aim 1 go/no-go**.

### A2 · Effect-size meta-analysis and power recalibration — *5–6 days*
**Question.** What effect size should n = 24/group actually be powered for?
**Data.** Europe PMC REST (verified live and unmetered). Anchor papers all open: Kapogiannis
2015 (PMC4314222), McIntyre 2025 (PMC12216818), Manolopoulos 2025 (PMID 40665589), Evers 2025
(PMID 40992133), Kapogiannis 2024 (PMC11305918), Malin 2025 (PMC11709104).
**Method.** R, `metafor`. Two-reviewer extraction with a **mandatory DISPERSION_TYPE column
adjudicated per paper** — Kapogiannis 2015 reports SEM, and mistaking SEM for SD inflates every
effect size by √n. Convert SD = SEM×√n, compute Hedges *g*, pool random-effects REML, report
τ², I² and a **prediction interval**. Pre-specified subgroups by normalisation scheme (CD81 vs
total protein), platform and population; leave-one-out and a Kapogiannis-lab-excluded
sensitivity analysis. Register on PROSPERO.
**Endpoint.** Pooled Hedges *g* with 95% prediction interval for pSer312-IRS-1 and for *R*;
secondarily, pooled correlation of nEV Akt/pAkt with HOMA-IR.
**Decision rule.** **Declare ONE primary endpoint** — recommended: pAkt-Ser473/total-Akt, or
*R* if continuity with the cited literature is preferred — with all others explicitly
exploratory and reported uncorrected. Frame Aim 2 as **effect-size estimation and a futility
test**, not a confirmatory comparison. If the pooled prediction interval spans null (the likely
outcome), say so: that is itself the publishable finding and the justification for the
follow-on sample size.
*Note: this is the one item that produces a manuscript submittable independently of any
wet-lab outcome. No such synthesis exists — a 2025 review screened 14,896 papers and pooled
nothing.*

### A3 · Brain:periphery specificity table and capture-antigen shortlist — *2–3 days*
**Question.** Is there a better antigen than L1CAM, and does the glial arm survive?
**Data.** GTEx v10 median TPM (public GCS bucket, 8.85 MB); HPA `search_download.php` API;
Walt-lab Norman 2025 repo; CZ CELLxGENE WMG v2 query API (pin the `snapshot_id`).
**Method.** Median NPX per SEC fraction against the CD63 control, using a **rank-based**
fractionation statistic rather than the published ratio (NPX is log2 and can be negative).
Cross-tabulate against DeepTMHMM topology and brain tau; compute a brain:periphery margin per
antigen from GTEx.
**Endpoint.** Ranked antigen list scored on (surface-accessible) × (EV-fractionating) ×
(brain-specific) ÷ (plasma soluble background), with L1CAM's position stated explicitly.
**Decision rules.** Replace GLAST with GFAP or ALDH1L1, or drop the glial arm and reallocate
to the ATP1A3 head-to-head. **Add a Schwann-cell counter-marker (PMP22 or MPZ)** and adipocyte
counter-markers (ADIPOQ, PLIN1) to the multiplex surface panel.

### A4 · MISEV2023 / MIBlood-EV compliance dossier — *2–3 days*
**Data.** MISEV2023 (Welsh 2024, JEV 13:e12404, PMC10850029) §3.4; MIBlood-EV (Lucien 2023,
JEV 12:e12385); EV-TRACK records EV140348, EV140333, EV170062, EV210415.
**Method.** Complete the MIBlood-EV form **before** any bench work; map the planned protocol
onto every EV-METRIC 2.0 item; set per-aliquot inclusion criteria.
**Endpoint.** A completed MIBlood-EV form for the grant appendix, a committed **EV-METRIC 2.0
target of ≥75%**, and stated aliquot criteria.
**Why it is worth a paragraph.** Quoting the founding paper's **19.44%** with a
particle-characterisation subscore of **0**, and committing to ≥75%, is nearly free and is
exactly what a MISEV-literate reviewer looks for. Two protocol changes follow regardless of
any analysis: **(i)** add a metalloprotease inhibitor from the moment of thaw and run capture
at 4 °C, time-limited *(as a precaution — note the vesicle-borne-ADAM10 mechanism is a
hypothesis, not an established finding)*; **(ii)** add a **matched isotype/anti-calnexin
capture arm at every input volume**, plus a biotin-blocking step.
*Caveat: an EV-TRACK ID cited by a recent paper did not resolve through EV-TRACK's public
search, so a deposited ID may not be publicly viewable — deposit, but do not lean on the ID
alone as evidence of rigour.*

### A5 · Re-analysis of the applicant's own PNOC TRAP-seq — *1–2 days*
**Data.** GSE137626 supplementary tables, direct from the GEO FTP.
**Output.** Preliminary-data figure: EV biogenesis machinery enriched in PNOC neurons; *Irs2*
enriched / *Insr* depleted; *Vamp2* and *Gap43* enriched (the single-EV neuronal validators of
Nogueras-Ortiz 2024). Yields a free panel correction — **CD81 as primary tetraspanin, CD9-low
reported as expected biology** rather than isolation failure.

### A6 · Proteome-Phenome Atlas lookup — *1–2 days, do if capacity allows*
`proteome-phenome-atlas.com`, free, no registration, ~50,000 UKB adults (HbA1c n = 50,148;
BMI n = 52,767; cystatin C n = 50,446). Look up GFAP, NEFL, L1CAM, IL6, NCAM1, SNAP25 against
HbA1c, glucose, adiposity and renal markers, with cystatin C and creatinine in the same matrix
to quantify the renal confound. **[V] Also look up INSR** — it *is* on the UKB Olink panel
(code 1439), so the "insulin-pathway protein in plasma tracks dysglycaemia" premise has a free,
zero-wet-lab test that nobody in this field has run.
**Say plainly what it cannot do:** marginal associations only. The discordance analysis is
intrinsically individual-level and this cannot deliver it.

---

## 3. Tier B — registration or short application

- **B1 · Synapse account for UKB-PPP pGWAS** (`syn51364943`; L1CAM `syn51469550`, GFAP
  `syn51471233`, NEFL `syn51469014`). Free account, minutes; anonymous download refused.
  **Day-1 triage: does any of L1CAM/GFAP/NEFL have a cis-pQTL passing p < 3.4e−11 with F > 10?**
  **Run this before writing any MR sentence into the grant** — if none does, every MR design
  collapses. The CSF side already fails: GFAP's best cis p ≈ 3e−5, NEFL has no cis signal, and
  the L1CAM file contains no chrX variants at all (L1CAM is X-linked).
  - Cheaper same-day pre-check, no account needed: two fully-open plasma L1CAM pGWAS with
    complete summary statistics exist in the GWAS Catalog — **GCST90101350** (n = 997) and
    **GCST90162025** (n = 2,935).
- **B2 · FinnGen DF13** (500,186 participants, 2,755 endpoints; browsing instant and free).
  A variant PheWAS of any L1CAM cis-pQTL is a same-day figure, free of UKB sample-overlap
  bias. Conditional on B1.
- **B3 · EV-TRACK deposition account.** One day, in October, so the ID can be quoted.

**Defer all of these** — each is 1–2 weeks of analyst time for a result that informs the
follow-on study, not this pilot: MetaBrain, ENIGMA-3, NIAGADS NG00102 *(note: it has an
open-access tier needing no DUA, and an announced portal outage 23–27 Sep 2026)*, ADNI/LONI,
deCODE, KORA, SCALLOP.

---

## 4. Tier C — formal application or collaboration: start now, harvest later

These are **future directions**, not pilot deliverables. Starting them in month 1 costs
nothing and demonstrates institutional competence.

| | Route | Lead time | Note |
| --- | --- | --- | --- |
| **C1** | **LIFE-Adult** — 10,000 deeply phenotyped adults **at the applicant's own university**, brain MRI in the >60 subgroup (n = 2,576 with hippocampal volume and BrainAGE; n = 1,581 with follow-up MRI) | internal email this week; weeks for data | The most under-exploited resource in this entire analysis. Cheaper and far more plausible than shipping DIRECT-PLUS samples from Ben-Gurion. **Check the LIFE data dictionary for fasting insulin before writing it in.** |
| **C2** | **DPPOS / NIA** (Kapogiannis, Mustapic) — nEV insulin-signalling on 456 prediabetes/T2D participants | 1–4 weeks for a reply; months for data | Real scoop risk. Position against it explicitly; a collaboration letter de-risks protocol transfer and assay comparability more than any analysis here. |
| **C3** | **Malin (Rutgers)** — the only group with nEV cargo *and* directly measured brain insulin action (pCASL) in the same people | weeks | The obvious validation partner. Their n = 15 result is the strongest existing support for the proposal. |
| **C4** | **INFINITE investigators** (McIntyre 2025) — individual-level *R* and HOMA2-IR, n = 71 | 2–8 weeks | The only route to a real joint distribution for the discordance analysis. A refusal costs nothing. |
| **C5** | **NAKO** — ~30,000 brain MRIs plus a live biosample application portal (`transfer.nako.de`); LIFE Leipzig hosts a NAKO study centre | months | The only realistic German path to nEV assays at population scale with paired brain MRI. |
| **C6** | **DZD / Tübingen** (Kullmann, Heni, Fritsche) — intranasal-insulin imaging; Helmholtz Munich is a DZD partner site | weeks | A domestic short path to a paired brain-insulin phenotype, and a letter of support worth more than the DIRECT-PLUS aspiration. |
| **C7** | **UK Biobank individual-level**, via the existing Helmholtz application | unknown | **Write this as summary-level work (A6) with the existing application named as the pathway — never as a new application, never as a pilot deliverable.** See the access caveat in [METHODS](METHODS.md#unverified-claims---check-before-use). |

---

## 5. Sequencing and gates

The critical path is **A1 → D1/D2/D4 → antibody and kit procurement → Aim 1 bench work →
A2 power → Aim 2 sample selection.** Everything else is parallel and non-blocking.

**Gate 1 — before any consumable order.** Matrix decided (D2). Capture panel decided:
5G3 + ATP1A3 + negative-capture control (D1). Platform and analytes decided, including pan-Tyr,
Ser616, Akt/ERK, NfL-for-GFAP (D4–D6). First-pass power numbers from A2.
> **Stop rule:** if the LOBB audit shows no matched plasma and aliquots average >2 freeze-thaws,
> **do not proceed to Aim 2 sample selection.** Reallocate Aim 2 budget into an Aim 1
> pre-analytical stability study (matrix × freeze-thaw × capture temperature × ± protease
> inhibitor). That is publishable, and it is the honest use of a compromised archive.

**Gate 2 — ~3 weeks in.** A4 dossier complete; MIBlood-EV form filed; EV-METRIC target
committed; A2 meta-analysis complete. **Single primary endpoint declared and pre-registered
(OSF), with a pre-specified discordance rule simulated against an r ≈ 0.19 null.** Without
this, Aim 2's headline claim is unfalsifiable.

**Gate 3 — mid-pilot, the decisive one.** The **proteinase-K protection assay**: intact SEC EV
fractions ± PK ± detergent, immunoblotted with a C-terminal/internal-domain L1CAM antibody,
CD81 as topology control.
> **Stop rule:** if no detergent-sensitive, PK-protected L1CAM C-terminal fragment is
> recoverable from LOBB material, **stop treating L1CAM as a vesicle marker.** Convert Aim 1
> into the antigen-benchmarking paper and run Aim 2 on the ATP1A3 arm only.

This is cheap, definitive, and publishable either way. Naming it as an explicit go/no-go
converts Aim 1's biggest weakness into its strongest design feature.

**Close-out deliverables.** MIBlood-EV form; EV-TRACK deposition; the meta-analysis manuscript
(independent of any wet-lab outcome); the Aim 1 methods manuscript; a defensible sample-size
estimate for the follow-on.

### Design work that costs nothing and is what a reviewer actually worries about
- **Bayesian assurance rather than frequentist power.** Priors span d = 0.40 (credible) to
  d = 4.0 (not). The honest instrument is a prior distribution over *d* and a
  probability-of-success calculation. The real deliverable of a 4-month pilot is a **posterior
  for *d***, not a p-value.
- **Pre-registration on OSF** with a decision tree and stopping rules, before samples are
  thawed.
- **Blinding and randomisation.** Interleave IR/IS across plates, blind the analyst, and run
  the pre-specified script on scrambled group labels first.
- **Consider a within-person design.** LOBB's longitudinal pre/post-bariatric structure
  removes between-person variance entirely and is far better powered at n = 24 than any
  two-group comparison.

---

## 6. Kill list

**Cut on timeline.** Any new UK Biobank application. China Kadoorie (4–5 month access pipeline
exceeds the grant). deCODE's 19.7 TB cross-platform release.

**Cut on capacity.** Full DIA-NN re-search of raw files from PXD040143, PXD076025 or PXD058777
(3–4 weeks each, for an analyst who does not exist — use the published supplementary tables
instead). The full 5,416-protein Walt-lab re-ranking beyond ~20 candidate antigens. MR across
~3,900 BIG40 brain IDPs. A full PRISMA systematic-review update — reduce it to the
effect-size meta-analysis, which is the part that powers the grant.

**Cut on value.** MetaBrain, ENIGMA-3, NIAGADS, ADNI, KORA, SCALLOP — all inform the follow-on,
none change what you buy in September. The GTEx L1CAM splice-isoform atlas is genuinely novel
and would be a good paper; in this document it reads as displacement activity. The IL6R
rs2228145 MR — expected T2D OR ≈ 0.98, and a 2025 critique argues the variant does not
faithfully proxy IL-6 signalling, so a null is uninformative.

**Cut on reliability.** ExoCarta (frozen at 2015; its entire human plasma/serum content is 145
entries across 104 genes, containing none of the target analytes — absence there carries no
information). Vesiclepedia gene pages without primary-source verification: its IRS1 "serum"
records derive from a *urinary nanovesicle* paper, and its L1CAM "plasma" records derive from
the paper that refutes L1CAM. **Do not cite either database without tracing the PMID and the
detection method.** EVpedia, exoRBase and ExoBCD were unreachable or unverifiable; the exRNA
Atlas (`exrna-atlas.org`, 11,174 processed samples) replaces exoRBase properly if an RNA
modality is ever wanted.

**Cut on being pre-empted.** A UKB obesity-subtype × plasma-proteome scan — Chami 2025 already
ran 2,920 Olink proteins × 30,271 participants against eight genetic obesity subtypes. The
residual novelty is the brain-specific framing, not the association testing.

---

## 7. What public data cannot do

Worth stating plainly, because the honest limits are what make the rest credible.

1. **No public dataset contains nEV cargo and obesity subtype together.** The pilot is not
   substitutable.
2. **HOMA-IR cannot be computed in UK Biobank.** The complete blood-biochemistry category is
   30 fields and contains **no insulin and no C-peptide assay**. Any UKB-based analysis must
   use HbA1c, glucose, or a surrogate index — not HOMA-IR.
3. **MR cannot touch the core hypothesis.** There is no pQTL for IRS-1 anywhere — absent from
   Olink Explore 3072 and HT, absent from SomaScan 7k, zero GWAS Catalog studies. And the one
   on-topic genetic result (the 2q36 *IRS1* locus acting through **adipose** IRS1 expression,
   explicitly not brain) argues *against* the proposal.
4. **A published null does not go away.** What public data *can* supply is the three legitimate
   reasons this pilot might succeed where McIntyre did not, and they should be stated
   explicitly: LOBB samples the **tails** of a deeply phenotyped subtype cohort rather than a
   mid-range HOMA2-IR ≈ 2.0 sample; McIntyre normalised to total protein by BCA while
   Kapogiannis normalised to CD81 — the leading candidate explanation for the 2.2–2.9-fold
   discrepancy in absolute *R* between labs, and **directly testable inside Aim 1**; and the
   analytes that *do* track HOMA-IR in obesity are Akt/pAkt/pERK, which the current panel omits.
5. **The brain-attribution gap is not closable in silico.** Only the mouse experiment in
   [`audit.md` §10](audit.md#10-the-gap-nobody-has-filled--and-the-applicant-is-uniquely-placed-to)
   closes it.

---

## 8. If only three things get done

1. **The LOBB inventory audit.** Not public data at all, and the most valuable dataset in the
   project. Does the matched design actually exist? What does BMI-matching cost in HOMA-IR
   separation? How many candidates have adequate volume and ≤1 freeze-thaw, in which matrix?
   Days of in-house work that could change — or invalidate — the design at zero cost.
2. **A2, the effect-size meta-analysis.** It converts n = 24/group from a convenience number
   into a stated minimum detectable effect, makes the "estimate effect sizes for a follow-on
   study" deliverable concrete rather than circular, and produces a manuscript regardless of
   what the bench does.
3. **The novelty rewrite plus the panel swap (D4/D5).** Both are paragraphs, not analyses.
   One removes the proposal's most dangerous vulnerability; the other is the single change most
   likely to convert a null pilot into a positive one.
