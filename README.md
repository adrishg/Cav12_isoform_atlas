# CaV1.2 Isoform Atlas

An evidence-tiered reference for **CACNA1C / CaV1.2** alternative splicing across human, rat and rabbit.

**Live site:** https://adrishg.github.io/Cav12_isoform_atlas/

The whole atlas is a **single self-contained HTML file**. No build step, no framework, no server.

## What it does

- **Exon atlas** — the seven loci that carry the tissue literature, with verified UniProt VAR_SEQ
  sequences, dual exon numbering, and every claim tiered by evidence quality.
- **Sequence checker** — paste a FASTA or multi-FASTA and get per-locus exon calls, an annotated
  topology figure for *that* sequence, and a report exportable as PDF, SVG, PNG or Markdown.
- **3D structure** — drop an AlphaFold `.pdb`/`.cif` and the spliced exons are painted onto it by
  residue range; colour by pLDDT confidence to see which parts of a prediction to trust.
- **Subunits** — which CaVβ and α2δ partner CaV1.2 in which tissue, and where splicing changes the
  answer.
- **Isoform builder** — pick an exon at each locus; find out whether that combination has ever been
  observed in native tissue.
- **Tissue map** — gene-level and transcript-level expression, kept strictly separate from
  isoform-level literature findings.
- **RNA regulation** — the RNA-binding proteins controlling each exon, developmental switches, sQTLs.
- **Papers** — 94 indexed papers, filterable by species, locus, method and evidence tier, with
  private reading marks and notes.

## Evidence tiers

Every claim carries one:

| Tier | Meaning |
|---|---|
| **1** | mRNA **and** protein detected in native tissue |
| **2** | Transcript evidence only (RT-PCR, RNA-seq, cloning) |
| **3** | Heterologous construct, or asserted without direct tissue evidence |
| **Disputed** | Papers actively contradict each other; both sides are cited |

## Updating the site

The GitHub repo is `adrishg/Cav12_isoform_atlas`; the local folder is
`~/Repositories/cav12-isoform-atlas`. The names differ, which is fine — the link
between them is the `origin` remote.

To publish a change, replace `index.html`, then:

```bash
cd ~/Repositories/cav12-isoform-atlas
git add index.html
git commit -m "describe the change"
git push
```

GitHub Pages rebuilds in about a minute.

If Pages is not yet serving, turn it on once: **Settings → Pages** →
*Build and deployment* → Source: **Deploy from a branch**, Branch: **`main`**,
folder: **`/ (root)`** → Save.

## Notes and privacy

Reading marks, stars and notes are stored in **your browser's local storage**. Nothing is uploaded,
and they do not sync between machines or browsers. Use **Back up notes** on the Papers tab to export
them as JSON, and **Restore from backup** to load them elsewhere.

The page makes no network calls of its own. It loads three things from public CDNs: web fonts from
Google Fonts, jsPDF from cdnjs (only when you export a PDF), and 3Dmol.js from jsDelivr (only for the
3D viewer). If any is blocked the page still works — fonts fall back to system faces, PDF export
falls back to Markdown with a notice, and the 3D tab says so and still shows its residue table.

The sequence checker **cannot query UniProt or NCBI** — it matches against reference segments held in
the page and hands your sequence to BLAST via a link. This is stated on the page itself; no result
claims to be a live database hit.

## Sources and honesty

Sequences are taken verbatim from UniProt VAR_SEQ records (Q13936 human, P15381 rabbit, P22002 rat)
or read first-hand from a paper. Nothing was reconstructed or transcribed from a rendered page.
Values restated from reviews rather than read from a primary table are marked as such. Known gaps are
listed on the References tab rather than filled in.

Every claim links to a PMID. If you find an error, that is the most useful thing you can report.

## Licence

Content is released under CC-BY-4.0 (see `CITATION.cff`). Change this if your lab or funder requires
something different.
