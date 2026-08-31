# How this was produced, and what to check

## Method

Eleven parallel research agents each scouted one domain (L1CAM validity; EV proteomics
repositories; large-scale plasma proteomics; genetics/MR; effect-size literature mining;
expression atlases; LOBB and obesity-subtype data; brain-insulin-resistance phenotypes; assay
and reagent feasibility; alternative in-silico designs; competitive landscape and novelty).
Each queried primary sources directly — REST APIs, FTP mirrors, GitHub repositories, PRIDE,
GEO, GWAS Catalog, Europe PMC, vendor catalogues — rather than answering from memory.

Their reports then went to three adversarial fact-checkers instructed to **refute**
load-bearing claims, prioritising accession numbers, panel-membership claims, access
conditions and any quantity that would enter a power calculation. Three critics (completeness,
grant-review, feasibility/sequencing) worked over the merged, fact-checked corpus.

Total: 17 agents, ~2.5 M tokens, 816 tool calls, no failures. Raw per-agent output is retained
in the workflow journal outside this repository.

The fact-checking mattered. It caught a mis-stated Zenodo DOI, a GEO SuperSeries that would
have silently pooled adipose with muscle, a mechanistic claim about ADAM10 that the cited paper
explicitly contradicts, a "paywalled" label on an open-access paper whose contents pre-empt a
proposed analysis, a tetraspanin recommendation contradicted by the scout's own source, and
two large published nulls that the primary literature scout missed entirely.

## Verification status

- **[V]** — verified by fetching the primary source in-session.
- **[V-]** — verified with a correction or caveat, stated inline.
- **[U]** — could not be verified from this environment.

Several sites were unreachable behind Cloudflare challenges or blocked egress, including
`ukbiobank.ac.uk`, `microvesicles.org` (Vesiclepedia), `exocarta.org`, NCBI's web interface
(the FTP and E-utilities routes worked) and the Wayback Machine. Where a claim depended on one
of those, it is marked **[U]** rather than quietly asserted.

## Unverified claims — check before use

These are the items that must not enter grant text until a human confirms them.

1. **UK Biobank RAP access status.** A scout reported the Research Analysis Platform shut in
   April 2026 with new applications suspended until "late 2026". **This could not be
   corroborated** — `ukbiobank.ac.uk` returned Cloudflare 403 to every route tried, and no
   search tool was reachable. A data point against over-reading it: the UKB Showcase
   (`biobank.ndph.ox.ac.uk`) was fully live and serving normally, though Showcase is
   metadata-only and says nothing about AMS/RAP. **Confirm by emailing UKB access support
   before writing anything about UKB availability either way.** It is load-bearing for the
   Tier C framing.
2. **Kapogiannis 2015 group means and SEMs.** PMC4314222 is outside the PMC open-access
   subset; three retrieval routes failed. The **abstract** confirms the design (26 AD, 20 DM2,
   16 FTD plus matched controls; 22 longitudinal converters; ELISA; ratio *R*) and that *R* was
   elevated in DM2. The **specific means, SEMs and the CD171/streptavidin-agarose capture
   detail are unverified** — and the d ≈ 4.0 reconstruction depends on them. Open the PDF
   before quoting any number from it.
3. **Vesiclepedia and ExoCarta content statistics.** Cloudflare 403 on both. The claim that no
   public EV database holds phosphosite data is **plausible but unconfirmed**. (A vendored
   copy of the ExoCarta table exists inside the Mag-Net repository if needed.)
4. **The Klein-lab MHO clamp threshold** (`GIR/I > 40`) is not in the GEO metadata and the
   paper is not open access. The GEO-stated definition is qualitative. Do not quote the number.
5. **Norman 2025 re-analysis details.** The paper's methods use only SEC fractions 7, 9, 10,
   11, 12, 13 for the EV call, so per-fraction values quoted outside that set need re-checking;
   and the paper's text says **57** unique transmembrane/internal EV-associated proteins, so
   the "295 proteins" figure must be re-derived from the repo before citation. The qualitative
   conclusion — CD63 early, L1CAM/NCAM1/CNTN2/CHL1/SNAP25/GAP43 late — is unaffected.
6. **A published NHANES TyG-vs-serum-NfL analysis** may already exist (PMC11984729, reported
   as n = 2,029). Check it before framing any NHANES rehearsal as novel.
7. **Two priors that look independent are not.** The "GFAP/NfL fall with adiposity" confound
   and the "brain glucose uptake rises with insulin resistance" construct hazard share a first
   author (Rebelos) and a site (Turku PET Centre). A reviewer familiar with that group will
   notice if they are presented as two independent lines of evidence.
8. **A cited UKB GFAP/NfL dementia study did adjust for prevalent diabetes** (BMC Medicine
   2024, PMID 38735950, n = 48,542). The correct statement of the gap is *"not adjusted for
   eGFR or continuous glycaemia"* — **not** "not adjusted for dysglycaemia".
9. **The cfRNA brain deconvolution reference is not open.** The `sevahn/deconvolution` README
   states the brain and liver cell atlases must be requested separately — i.e. the exact
   component this project would need is not freely available.
10. **OpenAlex is metered**, not free open infrastructure; it returned HTTP 429
    "insufficient budget". Europe PMC REST was reliably unmetered throughout and is the safer
    dependency for any literature-mining pipeline.

## Scope note

The two batched fact-checkers covering wet-lab feasibility and genetics/literature each
received three of four assigned scout reports because the input JSON was truncated at the size
cap. The `assay-feasibility` and `proposal-critique` scout reports were therefore **not
independently fact-checked**, and claims drawn from them — principally the vendor/catalogue
findings in [`audit.md` §6](audit.md#6-the-assay-plan-may-not-be-purchasable-as-written) and
the competitive-landscape findings in §9 — carry only their own author's stated confidence.
The two vendor calls in decision D4 resolve the most important of these directly.
