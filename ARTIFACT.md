# Artifact: Adaptive Speculative Decoding on a 24 GB Mac

This directory is the public artifact for the manuscript. It contains the paper, its
bibliography, its figure, and a machine-readable claim-to-evidence register. It does not
contain the raw measurement rows, the prompts, or the models.

## Contents

| File | Role |
| --- | --- |
| `manuscript.pdf` | The paper. |
| `manuscript.tex` | LaTeX source, generated from Markdown via Pandoc; builds with `tectonic`. |
| `references.bib` | Bibliography. |
| `figures/stock-results.svg`, `figures/stock-results.png` | Stock cap results and intervals. |
| `claims.csv` | One row per numerical claim: value, unit, verification depth, the SHA-256 of the raw artifact it was computed from, and that claim's stated limits. |

## Public evidence boundary

The source repositories and the raw personal prompts are private. This artifact gives
aggregate outcomes, method constraints, and SHA-256 checksums of the retained raw artifacts.
The raw rows are not published, so an independent reader cannot recompute the numerical
summaries from this artifact alone. No model weights, prompt text, prompt identifiers,
machine paths, per-request traces, or host process records are redistributed.

`claims.csv` records each claim's evidence location as a repository-relative or
symbolically-rooted path (`worktree:`, `whetstone:`, `legacy-checkout:`,
`external-volume:`) rather than a filesystem path. The accompanying `source_sha256` is the
checksum of the exact bytes the claim was computed from, so a reader who is later given a
raw artifact can verify it is the one used here.

## Models

The target is an MLX 4-bit conversion of `Qwen/Qwen3.8-27B`, distributed as
`mlx-community/Qwen3.8-27B-4bit` under Apache-2.0. The base model carries an Apache-2.0
LICENSE file; the conversion declares Apache-2.0 on its model card.

The drafter is a 4-bit round-to-nearest quantisation (group size 64, affine) of the
multi-token-prediction head from a third-party community fine-tune of the same base family,
also Apache-2.0 by its model card and also derived from `Qwen/Qwen3.8-27B`. Its repository
identifier and revision are recorded in the private artifact. It was the only
available MLX multi-token-prediction head for this family; see Section 3.2 of the manuscript
for why that choice does not affect what is measured. The local artifact carries a quantisation
provenance stamp (tool, source checksum, date). No model weights are redistributed here.

## Third-party components referenced

- **BANKING77** (Appendix A), used for an exploratory typed-decision comparison. Distributed as
  `PolyAI/banking77` under CC-BY-4.0, which requires attribution; this artifact reports counts and
  the dataset's public intent labels only, and no example text.
- **`bespokelabsai/nimble`**, the external typed-decision baseline in Appendix A. Its repository
  declares no license, so no redistribution right should be assumed; this artifact contains none
  of its code or outputs and refers to it by name only.
- **IFEval**, part of the public-sample recovery composite in Section 6.7. Distributed as
  `google/IFEval` under Apache-2.0.
- **WildBench**, the other part of that composite. `allenai/WildBench` declares no license on its
  dataset card and ships no LICENSE file; it is built from WildChat, which is distributed under
  ODC-BY. We treat ODC-BY attribution as the governing expectation and note the gap rather than
  assuming a broader grant.

This artifact redistributes none of their data: no prompt, response or example text from any of
them appears in it.

## Reuse

Text and figures in this artifact are available under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). This license covers this artifact
only. It grants no rights to the private datasets, the models, or any third-party software
named above.
