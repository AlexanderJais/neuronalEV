# The reference nEV protocols, verbatim

**There are two, and they are not the same.** The Kapogiannis lab has moved on from the method
our proposal describes. Both are given below, from the primary sources.

| | **Protocol A** — Malin 2025 | **Protocol B** — Kapogiannis 2024 |
| --- | --- | --- |
| Source | *Aging Cell* 24:e14369, PMID 39421964 (CC-BY, full text) | *Cell Metab* 36(8):1668–1678.e5, PMID 38901423 (author manuscript) |
| EV separation | **ExoQuick precipitation** | **Size-exclusion chromatography (30–1000 nm)** |
| Capture antigens | **L1CAM alone** (clone 5G3) | **L1CAM + GAP43 + NLGN3** (three antigens) |
| n | 21 | 40 |

> **This matters for Aim 1.** Our proposal specifies single-antigen L1CAM immunocapture — that is
> Protocol A, the older one. The same lab's 2024 trial uses SEC first and then captures on
> **three** neuron-specific antigens. Given the L1CAM evidence in
> [`audit.md` §1](audit.md#1-the-l1cam-problem-is-worse-than-a-controversy), proposing the
> superseded single-marker version is a gift to a reviewer. Multi-antigen capture is also
> convergent with the ATP1A3 head-to-head in decision D1.

---

## Protocol A — Malin 2025 (ExoQuick + L1CAM alone)

§2.6 *nEV isolation* and §2.7 *Biomarker determination*, from the Europe PMC full text.

## Matrix

**EDTA plasma.** The paper states *"Insulin and nEV EDTA vacutainers contained aprotinin."*
Plasma is then **defibrinated with thrombin** before isolation.

> This settles the serum-vs-plasma inconsistency in our proposal (Aim 1 says serum, the
> September work programme says plasma). No published L1CAM-nEV study uses serum. If LOBB
> holds only serum, that is a protocol deviation requiring its own validation — not a detail.

Reagent volumes below are **per 100 µL of starting plasma**. The authors note volumes were
normalised to input plasma volume throughout, *"thus ensuring that biomarker outcomes were not
confounded by nEV recovery."*

## Isolation

| # | Step | Reagent / setting |
| --- | --- | --- |
| 1 | Defibrinate | 1.2 µL thrombin (System Biosciences **TMEXO-1**), 30 min RT |
| 2 | Dilute | 98.8 µL Dulbecco's PBS 1× + 2× protease (Roche cOmplete, **04693116001**) + Halt phosphatase inhibitors (Thermo **78427**) |
| 3 | Clear | 6,000 × g, 20 min, RT — keep supernatant |
| 4 | Precipitate total EVs | 50.4 µL ExoQuick (SBI **EXOQ100A-1**), 60 min RT → 1,500 × g, 20 min, 4 °C |
| 5 | Resuspend crude EVs | 140 µL ultra-pure distilled water + 1× protease/phosphatase inhibitors, **overnight** gentle rotation at 4 °C |
| 6 | **Immunocapture** | **0.8 µg biotinylated anti-human L1CAM, clone 5G3, Thermo Fisher 13-1719-82**, 120 min at 4 °C |
| 7 | Pull down | 5 µL washed Pierce Streptavidin Plus UltraLink Resin (Thermo **53117**), 60 min 4 °C, gentle rotation |
| 8 | Wash / collect | 600 × g, 10 min, 4 °C; discard supernatant |
| 9 | Elute | 40 µL 0.1 M glycine (from 1 M stock, pH 2.7; Polysciences **24074-500**), vortex 10 s |
| 10 | Separate beads | 4,500 × g, 5 min, 4 °C; transfer supernatant |
| 11 | Neutralise | 6 µL 1 M Tris-HCl pH 8 (Fisher, CAS 1185-53-1) — **immediately** |
| 12 | Lyse | Two freeze–thaw cycles in 10 µL 3% BSA + 48 µL M-PER (Thermo **78501**) + 2.2× protease/phosphatase inhibitors; store −80 °C |

## Assays — MSD, not Simoa

| Analyte | Platform | Catalogue |
| --- | --- | --- |
| **pAkt (Ser473) / total Akt** | MSD electrochemiluminescence | **K15100D** |
| **p-IRS-1 Ser312** | MSD | **150HLD** |
| pERK1/2, pJNK, pp38 (MAP Kinase phosphoprotein panel) | MSD | **K15101D** |
| proBDNF | ELISA | Biosensis BEK-2237 |

Read on a MESO QuickPlex SQ120; Workbench 4.0. Samples run in **duplicate**, input set by
prior dilution-optimisation experiments to land within each assay's dynamic range; four-parameter
logistic standard curves.

> **Every published nEV IRS-1 / Akt measurement uses MSD, ELISA, Western blot or Luminex.**
> No Simoa assay for IRS-1 or phospho-Ser312-IRS-1 could be located. Our budget line reading
> "by Simoa or MSD" should be corrected to MSD, with these catalogue numbers.

## Characterisation the protocol relies on

The paper does not re-characterise the preparations. It cites **Delgado-Peraza 2023** and
**Vreones 2023** as having shown *"the purification of nEVs of expected size from free plasma
components, as well as the enrichment of L1CAM+ EVs co-carrying bonafide neuronal markers."*

Read those two before adopting the protocol — they are the entire characterisation basis, and
they are what the counter-evidence in [`audit.md` §1](audit.md#1-the-l1cam-problem-is-worse-than-a-controversy)
disputes. **Note there is no isotype or irrelevant-antigen capture control anywhere in this
workflow.** Adding one is our cheapest, highest-value deviation.


---

## Protocol B — Kapogiannis 2024 (SEC + three-antigen capture)

Verbatim from the STAR Methods, *NDEV MEASURES*:

> *"Briefly, a two-step procedure was followed. First, we used **size exclusion chromatography
> (SEC)** to purify total EVs from soluble material and particles outside the 30–1000 nm range.
> Second, enrichment for neuronal EVs was performed via immunoaffinity capture targeting **three
> neuron-specific antigens**: L1 Cell Adhesion Molecule (L1CAM), the axonal protein
> Growth-Associated Protein 43 (GAP43), and the dendritic protein Neuroligin 3 (NLGN3), using a
> variation of the method described by Eitan et al."*

Full step-by-step is in their Methods S1 (supplement), not the main text — **request it**.

### Reagents, from the STAR Methods resource table

| Item | Source | Catalogue |
| --- | --- | --- |
| Biotinylated anti-human CD171 (L1CAM), **clone 5G3** | eBioscience | 13-1719-82 |
| **anti-GAP43 + anti-NLGN3 "ExoSORT" mix** | NeuroDex | **not commercially available** |
| anti-NCAM1 | Thermo Fisher | A51017 |
| anti-CD9 / anti-CD63 / anti-CD81 | BioLegend | 322107 / 353007 / 349509 |
| Human Tetraspanin **ExoView** kit | NanoView Biosciences | EV-TETRA-C |
| Albumin ELISA · ApoA1 ELISA (purity controls) | Abcam | ab179887 · ab108803 |
| Uranyl acetate (EM) · CellTrace Violet | Ted Pella · Thermo | NC1630601 · C34557 |

> **The GAP43/NLGN3 antibodies are not purchasable.** Exact replication of Protocol B requires a
> NeuroDex agreement. Worth an email before committing Aim 1 to any capture strategy.

### Assays — which platform for which analyte

| Analyte | Platform | Catalogue |
| --- | --- | --- |
| **pS312-IRS-1** | MSD | **C10HL-1** |
| **pY-IRS-1 (pan-tyrosine)** | MSD | **K150HDL** |
| **Akt + pS473-Akt** | MSD | **K15100D** |
| pERK1/2, pJNK, pp38 | MSD | K15101D |
| Aβ42, Aβ40, total Tau | **Simoa** | Quanterix Neurology 3-Plex A |
| p181-Tau | **Simoa** | Quanterix 104111 |
| **NfL and GFAP** | **Simoa** | Quanterix 102153 |
| proBDNF | ELISA | Biosensis BEK-2237 |
| Mitochondrial complex IV / V | ELISA | Abcam ab109910 / ab109716 |

Two corrections to our proposal follow directly:

1. **"By Simoa or MSD" is half right.** This lab uses **Simoa for GFAP and NfL**, and **MSD for
   every IRS-1 and Akt measurement**. There is no Simoa IRS-1 assay in their workflow. Budget
   accordingly: Simoa line for GFAP/NfL, MSD lines for the insulin-signalling panel.
2. **The pan-Tyr arm we are missing has a catalogue number: MSD K150HDL.** Add it, or drop the
   ratio language. *(Note a discrepancy between sources: Malin 2025 cites "150HLD" for pS312
   while Kapogiannis 2024 cites C10HL-1 for pS312 and K150HDL for pY-IRS-1. Confirm both with
   MSD before ordering.)*

### MISEV characterisation package worth copying

ExoView tetraspanin chip (CD9/CD63/CD81), transmission EM with uranyl acetate, CellTrace Violet
labelling with flow cytometry, plus **albumin and ApoA1 ELISAs as soluble-contamination
controls**. That is a defensible MISEV2023 package and it is cheaper to copy than to design.

**Still absent from both protocols: an isotype / irrelevant-antigen capture control.** Adding one
remains our single cheapest, highest-value deviation.

### Data availability

The paper states all shareable datasets were deposited in **Mendeley Data**. The link printed in
the resource table is a *preview* URL
(`data.mendeley.com/preview/nmgr63z5wy?a=d54ae508-…`) and it **returns HTTP 401 — expired or
private [V]**. Trial registration is **NCT02460783**.

> This dataset is worth chasing by email (lead contact: kapogiannisd@mail.nih.gov). It would
> contain nEV insulin signalling, BrainAGE, MRS brain glucose and HOMA2-IR **in the same 40
> people** — see [`audit.md` §4a](audit.md#4a-what-has-actually-been-measured-against-a-brain-readout)
> for why that combination is the one that matters.
