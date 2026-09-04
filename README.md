# nEV liquid biopsy of brain insulin resistance — public-data & data-mining plan

Companion analysis for the 2026 LeiCeM Mini Flex proposal *"Neuron-derived extracellular
vesicles as a liquid biopsy of brain insulin resistance across obesity subtypes"*
(A. Jais, HI-MAG / University of Leipzig; mentor M. Blüher; 01.09.–31.12.2026; €24,550).

## The short answer

**Yes — and more than expected.** Public data can do four distinct jobs here:

1. **De-risk Aim 1 before a single aliquot is thawed.** Whether L1CAM immunocapture
   isolates vesicles at all is answerable *today* from open datasets, and the answer
   currently leans negative.
2. **Supply the effect size Aim 2 is missing.** `n = 24/group` is not justified anywhere in
   the proposal. The published record supplies the priors, and they are far smaller than the
   founding paper implies.
3. **Re-optimise the analyte panel for free.** Two independent obesity cohorts show the
   analytes that track HOMA-IR are Akt/pAkt/pERK — none of which the current panel measures.
   Note carefully: those are **peripheral** correlations. **No nEV analyte has been shown to
   measure central (brain) insulin resistance** — see [`docs/audit.md` §4a](docs/audit.md).
4. **Establish what is actually novel.** The novelty claim as written is refuted by at least
   three published cohorts, one of them null on the exact primary endpoint at larger *n*.

What public data **cannot** do is substitute for the pilot. There is no public dataset
containing nEV cargo and obesity subtype together, and no amount of mining makes a published
null disappear.

## Documents

| File | What it is |
| --- | --- |
| [`docs/audit.md`](docs/audit.md) | What the mining already established — the facts that change the proposal *before* any new analysis |
| [`docs/plan.md`](docs/plan.md) | The work plan: packages A/B/C by access tier, decision gates, critical path, kill list |
| [`docs/resources.md`](docs/resources.md) | Verified resource inventory — accessions, URLs, access conditions, verification status |
| [`docs/protocol-reference.md`](docs/protocol-reference.md) | The two published nEV protocols verbatim, with catalogue numbers — including the one our proposal has superseded |
| [`docs/METHODS.md`](docs/METHODS.md) | How this was produced, and the verification caveats that apply to every claim here |

## How to read the claims

Every factual claim carries a status marker:

- **[V]** verified in-session by fetching the primary source
- **[V-]** verified with a stated correction or caveat
- **[U]** could not be verified from this environment — **confirm before it enters grant text**

Nothing here should reach a submitted document without the applicant checking the **[U]**
items. They are listed together in [`docs/METHODS.md`](docs/METHODS.md#unverified-claims---check-before-use).
