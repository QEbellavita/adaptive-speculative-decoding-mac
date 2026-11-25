# Adaptive Speculative Decoding on a 24 GB Mac

**Lossless in Theory, Divergent in Practice: Does Adaptive Speculative Decoding Actually Pay Off?**
Working draft, 29 September 2026.

A preregistered evaluation of adaptive draft-length selection for speculative decoding with MLX on
one Apple Silicon Mac with 24 GB of unified memory. In short:

- Speculative decoding is described as lossless, but in this implementation 9 of 20 requests
  differed from plain (solo) decoding.
- The adaptive policy cut mean latency by 4.50% against a fixed draft length of 5
  (95% interval 0.49–8.52%), which missed the registered 5% practical-gain threshold.
- A test of self-distilling the drafter on the owner's own traffic came back **inconclusive**.

The paper reports what did not work alongside what did, and lists the open questions
(fresh-request confirmation, the numerical cause of divergence, and replication on a second machine).

## Contents

| File | What it is |
| --- | --- |
| [`manuscript.pdf`](manuscript.pdf) | The paper (20 pages). |
| `manuscript.tex`, `references.bib` | LaTeX source and bibliography. |
| `figures/` | Results figure (SVG and PNG). |
| [`claims.csv`](claims.csv) | Every numerical claim with its value, limits and the SHA-256 of the raw artifact it came from. |
| [`ARTIFACT.md`](ARTIFACT.md) | What this artifact does and does not contain. |

## What is not included

The source repositories, raw measurement rows, prompts and model weights are private and are not
redistributed here. `claims.csv` gives checksums so a reader later given a raw artifact can confirm
it is the one used. See `ARTIFACT.md` for details.

## Licence

MIT. See [`LICENSE`](LICENSE).
