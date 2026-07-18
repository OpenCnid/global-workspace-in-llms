# AGENTS.md

> Instructions for AI agents working in or consuming this repository. Human?
> The [README](README.md) is friendlier.

## What this repo is

One paper, studied. [density-chain.md](density-chain.md) is a five-tier
chain-of-density note on Gurnee et al., *Verbalizable Representations Form a
Global Workspace in Language Models* (Transformer Circuits Thread, published
July 6, 2026). The methodology lives canonically in
[chain-of-density](https://github.com/OpenCnid/chain-of-density) — METHOD.md,
the synthesis prompt, and the `density-chain` skill — and is linked, never
copied.

## Consuming the research

- **Pick your tier by information need, not length.** T1 through T5 are the
  same length (budget in the note's frontmatter); each tier folds in more
  entities. Skim with T1, work with T5.
- **The note is working ground truth; the paper is canonical.** On any doubt
  or high-stakes claim, the paper wins. Every claim carries a locator — this
  source is a lab article, so locators are section headings, not page
  numbers. Walk them back in one hop.
- **Check freshness.** The source is a web publication with no version
  number; the pin is the publication date plus the URL, and the frontmatter
  carries `verified_against_source`. Web pages can be revised silently — if
  staleness matters, re-verify at the canonical URL.
- **`index.json` is the machine face.** Pins, verification dates, tags,
  paths. Parse it; don't scrape the markdown.
- **Cite the humans, not this repo.** The paper's own BibTeX is in
  [CITATION.md](CITATION.md).
- A checksum-verified PDF snapshot of this paper exists at
  [verbalizable-global-workspace-pdf](https://github.com/OpenCnid/verbalizable-global-workspace-pdf)
  as an acquisition artifact; the canonical rendering — and the one this
  note's locators follow — is the live Transformer Circuits page.

## Working on this repo

- To update the note, invoke the `density-chain` skill from the
  chain-of-density repo; study the paper at the canonical URL; write nothing
  from memory.
- Downloaded copies are session study material: scratchpad only, never
  committed here.
- Humor belongs in the README and the note's *our take* section only. Tiers,
  key results, and provenance stay bone-dry.
- Authority runs **paper → note → inspirations entry**, one direction.

## Your team, your rules

This file describes how the repo is designed to be used, not the only way to
use it. The invariants that protect correctness: the source wins, claims keep
their locators, and citations go to the humans who did the work.
