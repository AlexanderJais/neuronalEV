# Verified resource inventory

Everything below was checked by fetching the primary source during this analysis, unless
marked **[U]**. Sample sizes, accessions and access conditions are quoted as found.

## Tier A — fully open, no registration

### EV proteomics and methodology

| Resource | Accession / URL | Contents | Answers |
| --- | --- | --- | --- |
| **Mag-Net plasma EV proteome** | PXD042947 · `github.com/uw-maccosslab/manuscript-mag-net` · Zenodo 10.5281/zenodo.15273142 | Released Skyline matrices: 2,343 protein groups × 48 runs (EV), 4,675 groups (EV + neat plasma), per-protein LOD/LOQ for 3,855 proteins | Peptide topology per antigen; whether IRS1/INSR are detectable at all (**they are not**); ATP1A3 detected 48/48 |
| **Norman 2025 SEC-Olink CSF** | PMC11913887 · `github.com/Walt-Lab/ev_association_olink_analysis` (GPL-3.0) | 5,416 proteins × SEC fractions 6–15, 4 CSF donors; raw NPX parquet, plate map, DeepTMHMM topology, BrainRNA-Seq, GTEx v10 medians | Is L1CAM EV-associated? Ranked capture-antigen triage |
| **Kadam 2025 CSF EV proteomics** | PXD058777 · PMID 40210837 · PMC12289729 | Independent replication using clone 5G3; SEC + polymer precipitation, NTA, WB, Simoa NfL, LC-MS | L1CAM IP yields no enrichment; NfL *is* in CSF/blood EVs; transferable pre-clearing SOP |
| **EV-TRACK** | `evtrack.org` | EV140348 (Kapogiannis 2015, EV-METRIC 2.0 = **19.44%**, particle subscore 0); EV170062 (Mustapic 2017, 58.55%); EV140333; EV210415 | Reporting quality of the founding studies; the benchmark to commit to |
| **MISEV2023 / MIBlood-EV** | Welsh 2024 JEV 13:e12404 (PMC10850029) · Lucien 2023 JEV 12:e12385 | Reporting frameworks | What Aim 1 must report |
| **Serum EV proteome in obesity/diabetes** | PXD040143 (Lee 2025, *Int J Obes* 49:1874–1881) | 12 obese with diabetes, 18 without, pre/post bariatric, + 37 controls; ExoQuick from 1 mL serum | Per-protein variance prior in the matrix LOBB actually holds. **Use published supplementary tables — do not re-search raw** |
| **L1CAM-IP plasma nEV DIA** | PXD076025 | 1,354 proteins, 28 subjects | Only if a processed report is deposited. **[U]** Instrument metadata conflict; PARTIAL submission; Parkinson's cohort with no metabolic phenotyping — email the submitters instead |

### Expression atlases

| Resource | URL | Notes |
| --- | --- | --- |
| **GTEx v10 median TPM** | `storage.googleapis.com/adult-gtex/bulk-gex/v10/rna-seq/GTEx_Analysis_v10_RNASeQCv2.4.2_gene_median_tpm.gct.gz` | 59,033 genes × 68 tissues incl. 13 brain regions, tibial nerve, both adipose depots. 8.85 MB |
| **Human Protein Atlas API** | `proteinatlas.org/api/search_download.php` | Tissue/single-cell/blood specificity classes, per-region brain nTPM |
| **CZ CELLxGENE WMG v2** | `api.cellxgene.cziscience.com/wmg/v2/query` | Per-cell-type detection fraction. Brain ~26.7 M cells, blood ~25.1 M, adipose ~449 k. **Pin the `snapshot_id`** — counts move |
| **Human HYPOMAP** | CELLxGENE collection `d0941303-7ce3-4422-9249-cf31eb98c480` | 433,369 human hypothalamic nuclei, 11 donors, 452 cell types |
| **GSE137626** | GEO FTP `series/GSE137nnn/GSE137626/suppl/` | The applicant's own PNOC BacTRAP, chow + HFD, public since 2020 |
| **GSE161355** | GEO | 6 T2D vs 5 controls, laser-captured human cortical neurons/astrocytes/endothelium |
| **GSE301739** (SuperSeries: GSE301735 + GSE301736) | GEO | **Blood DNA methylomes of brain-insulin-**RESISTANT** vs **SENSITIVE** humans** (Kullmann/Heni/Birkenfeld), participants **without** T2D, detailed metabolic phenotyping. A competing peripheral classifier of brain IR — and a carve-out for a T2D-inclusive nEV study |
| **GSE244118** | GEO | **20 MHO vs 20 age/sex/BMI-matched MUO**, abdominal adipose RNA-seq, 53 samples. **[V-] Use GSE244118, not the GSE244121 SuperSeries** — the latter pools adipose with 50 thigh-muscle samples |

### Genetics (summary statistics)

| Resource | URL / accession | Notes |
| --- | --- | --- |
| **MAGIC glycaemic traits** | `magicinvestigators.org/downloads/` | Chen 2021 trans-ancestry, up to 281,416 non-diabetic, BMI-adjusted; Lagou 2021 sex-dimorphic; Williamson 2023 post-challenge insulin sensitivity |
| **GIANT anthropometrics** | `giant-consortium.web.broadinstitute.org/GIANT_consortium_data_files` | Pulit 2019 BMI and WHRadjBMI, sex-stratified |
| **Oxford BIG40 brain IDPs** | `open.win.ox.ac.uk/ukbiobank/big40/release2/stats33k/<IDP>.txt.gz` | ~3,929 IDPs, n ≈ 33k, no registration. **[V-]** "33k" is the site's own wording |
| **Western 2024 CSF pQTL** | GWAS Catalog, PMID 39528825; L1CAM = GCST90425991 | n = 3,506, SomaScan 7k. **GFAP best cis p ≈ 3e−5; NEFL no cis signal; the L1CAM file has no chrX variants** |
| **Open plasma L1CAM pGWAS** | GCST90101350 (n = 997); GCST90162025 (n = 2,935) | Fully open, complete summary statistics. Cheapest possible day-1 cis-pQTL existence check |
| **GWAS Catalog REST + FTP** | `ebi.ac.uk/gwas/rest/api/` | Establishes definitive negatives — e.g. **no IRS1 pGWAS exists anywhere** |
| **ONTIME brain/CSF/plasma pQTL** | `ontime.wustl.edu` · NIAGADS NG00102 | CSF n = 835, plasma n = 529, brain n = 380. **[V-]** NG00102 has an **open-access tier needing no DUA**; portal outage announced 23–27 Sep 2026 |

### Phenotype browsers

| Resource | URL | Notes |
| --- | --- | --- |
| **Proteome-Phenome Atlas** | `proteome-phenome-atlas.com` | Free, no registration, ~50,000 UKB adults. HbA1c n = 50,148; BMI n = 52,767; cystatin C n = 50,446 |
| **FinnGen DF13** | `r13.finngen.fi` | 500,186 participants, 2,755 endpoints; browsing instant, bulk needs a one-page form |
| **exRNA Atlas** | `exrna-atlas.org` | 11,174 processed samples across 5 biofluids; the proper replacement for exoRBase |
| **Reinisch 2025 MHUO browsers** | `github.com/WolfrumLab/MHUO` | LOBB-adjacent obesity-subtype Shiny apps. **[U]** Repo contents could not be listed (403) — do not promise a specific table format |

### Panel membership — checked, and worth knowing before proposing a lookup

**On** UK Biobank Olink (Data-Coding 143, 2,922 assays, n = 53,039): **INSR (1439)**,
NEFL (1840), SNAP25 (2507), APP (159), ENO2 (926), TUBB3 (2802), GFAP, IL6, L1CAM.
**On Explore HT but NOT on UKB:** GAP43, PLP1. **On neither:** S100B, **SLC1A3/GLAST**,
**IRS1** (also absent from SomaScan 7k).

> **[V] UK Biobank has no insulin and no C-peptide assay.** The complete blood-biochemistry
> category is 30 fields; HbA1c (30750) and glucose (30740) are there, insulin is not.
> **HOMA-IR cannot be computed in UKB.**

## Tier B — free registration

- **UKB-PPP pGWAS on Synapse** — `syn51364943` (OPEN, free account; anonymous download
  refused). European discovery folder `syn51365303`; L1CAM `syn51469550`, GFAP `syn51471233`,
  NEFL `syn51469014`. **[V-]** Summary statistics need only an account; **individual-level
  Olink NPX needs a paid UK Biobank application** — two very different timelines.

## Tier C — application or collaboration

**LIFE-Adult** (Leipzig University — 10,000 adults, brain MRI in the >60 subgroup, PMID
26197779) · **NAKO** (`transfer.nako.de` — separate MRI and biosample application tracks) ·
**Rhineland Study** (DZNE Bonn, up to 20,000) · **IMI DIRECT** (clamp-phenotyped) ·
**NIDDK Central Repository DPP/DPPOS** (`repository.niddk.nih.gov/study/40`) ·
**DIRECT-PLUS** (Ben-Gurion, MTA-level).

## Assays and reagents

- **Capture antibody:** biotinylated anti-L1CAM clone **eBio5G3, cat. 13-1719-82** — used by
  both Kapogiannis and the Kadam replication. **[V]** Not in the YCharOS knockout-validated
  corpus.
- **[V] No Simoa assay for IRS-1 or pSer312-IRS-1** could be found in the Quanterix catalogue.
- **[V] Invitrogen KHO0521** reports **arbitrary U/mL with no absolute standard**, validated
  for **cell lysates only** — serum and plasma are not listed matrices.
- **MILLIPLEX Akt/mTOR 11-plex** carries pIR, pIRS-1-Ser636, pAkt-Ser473, total Akt, pERK1/2,
  pTSC2, p-p70S6K.
- **Multiplex EV surface profiling:** confirm the exact kit and its platform against the
  €1,850/96-test budget line and the flow-core line before submission.
