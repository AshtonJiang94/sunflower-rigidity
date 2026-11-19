# Sunflower Detectors: MDS Classification, Layered Optimization, and the Limits of Envelope Counting

JIANG ZHICHENG — ORCID: [0009-0001-4772-4490](https://orcid.org/0009-0001-4772-4490)

This repository contains the paper and the complete verification code for an
optimization of the vector sunflower interpolation of Bucić, He and Lee
(arXiv:2610.26686v1).

> Cite as: JIANG ZHICHENG, *Sunflower Detectors: MDS Classification, Layered
> Optimization, and the Limits of Envelope Counting*, 2026.
> DOI: [10.5281/zenodo.24373110](https://doi.org/10.5281/zenodo.24373110)
> (reserved 2026-11-19; activates on publication).
> arXiv: forthcoming (endorsement pending).

## Results

- **MDS classification (Theorem 4).** For arbitrary specified MDS evaluation
  spaces, an anchored detector exists if and only if the sorted dimensions
  satisfy $d_i \ge i$ for all $i$; the affine dimension is
  $D[(D-1)\cdots(D-m)-\prod_i(D-d_i)]$. The minimal profile is unique.
- **Even-petal rigidity (Theorem 6).** Over ordered fields, an even number of
  petals satisfies the all-direction rigidity criterion
  ($\sum d_i \ge k(k-1)/2$). Odd petals (Proposition 7) and a four-element
  field (Proposition 20) show the hypotheses are essential.
- **Four-petal bound (Proposition 13).**
  $F_4(N) < 2.312\cdot 1.988772^N$, certified by exact integer arithmetic.
- **Large-petal limit (Theorem 17).** The optimal saving of the random-block
  reduction is $(\gamma+o(1))/m^3$ with $0.34938 < \gamma < 0.34940$,
  certified by interval arithmetic.

Scope, stated in the paper: optimality is within full-profile, term-by-term
covering in a fixed letter basis. It does not change the exponent
$1-1/(k-1)$, does not give a new detector, and does not resolve the
Erdős–Rado conjecture. For $k=3$ this method does not beat the existing
specialized triangular-tensor bound (Ahmadi–Norouzi, Theorem 1.4).

## Files

- `Sunflower_Integrated_Structure_and_Optimization_EN_20261117_1028_SUB.pdf`
  — research manuscript, 22 pages (English; MSC 05D05; ORCID in author footnote).
- `Sunflower_Original_Proof_Reconstruction_EN_20261117_1028.pdf`
  — self-contained reconstruction of the Bucić–He–Lee exponential bound, 8 pages.
  A companion, not an independent solution of the conjecture.
- `sunflower-20261117_1028-package.zip` — the full reviewed package (57 files):
  manuscripts (EN + CN, tex + Word), verification code, certificates, logs,
  revision record, SHA-256 manifest.

## Reproduce

Python 3.12, in a clean directory, never with `python -O`:

```bash
# Five exact / finite checks (no third-party packages needed)
python verify_all.py --mode quick

# Everything, including the two Arb interval certificates
python -m pip install -r requirements.txt   # numpy, scipy, python-flint
python verify_all.py --mode full
```

Results are written to `run_results.json` and `logs/`. Reference outputs from
the reviewed run are in the package (`run_results.json`: 7/7 PASS).

## Evidence levels

1. **Exact certificates** — integer/rational comparisons, standard library only.
2. **Interval certificates** — Arb outward rounding (`certify_*.py`); floating
   point only proposes candidates.
3. **Finite checks** — `verify_rigidity_v2.py`, `verify_proof_chain.py`,
   `verify_new_structure.py`; they test formulas, they do not replace the
   all-parameter proofs.
4. **Exploratory** — finite-field searches; a failure over a finite field does
   not transfer automatically to characteristic zero.

No Lean or other formal proof checker was used. No independent peer review
has been completed yet.

## License

Paper: CC BY 4.0. Code: MIT.
