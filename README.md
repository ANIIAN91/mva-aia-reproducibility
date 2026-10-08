# Versioned AIA reproducibility entry

## Releases

| Version | Date | Contents |
|---|---|---|
| [v1.3.0](https://github.com/ANIIAN91/mva-aia-reproducibility/releases/tag/v1.3.0) | 2026-10-08 | Delta to v1.2.2: frozen protocols, code, configurations and results of the experiments run after v1.2.2 (codes DA-DH: AIA coefficient, start and training length; single test evaluation of the same-experiment peer comparison; evaluation on a second white-button source without retraining; re-scoring of archived predictions for leakage on common matches, mask-area size bins and touching/isolated instances), and the current Online Resource 2 with these tables in `source_data/review2`. Run `python verify_release.py` in the extracted `mva_aia_reproducibility_v1.3.0` directory. |
| [v1.2.2](https://github.com/ANIIAN91/mva-aia-reproducibility/releases/tag/v1.2.2) | 2026-10-05 | Delta to v1.2.1: code, configurations, frozen protocol and results of the class-stratified resampling (seeds and BB acquisition groups resampled, the single WB group kept), and the current Online Resource 2 with the two derived tables added. Run `python verify_release.py` in the extracted `mva_aia_reproducibility_v1.2.2` directory. |
| [v1.2.1](https://github.com/ANIIAN91/mva-aia-reproducibility/releases/tag/v1.2.1) | 2026-10-05 | Patch to v1.2.0: the current Online Resource 2 of the manuscript. Its data files are identical to the copy in v1.2.0; only its README changes (final article title). Run `python verify_release.py` in the extracted `mva_aia_reproducibility_v1.2.1` directory. |
| [v1.2.0](https://github.com/ANIIAN91/mva-aia-reproducibility/releases/tag/v1.2.0) | 2026-10-05 | Delta to v1.1.0: code, run configurations, frozen protocols and numerical summaries of the random-owner-point and same-experiment peer comparison, the four pipelines on StrawDI_Db1 and MinneApple, and the seed x acquisition-group resampling intervals; Online Resource 2 of the manuscript with these derived tables. Run `python verify_release.py` in the extracted `mva_aia_reproducibility_v1.2.0` directory. |
| [v1.1.0](https://github.com/ANIIAN91/mva-aia-reproducibility/releases/tag/v1.1.0) | 2026-10-02 | Delta to v1.0.0: AIA source at the commit bound by all later training rounds; code, run configurations, frozen protocols and numerical summaries of the scale-expansion, P2, pairwise-affinity veto and single-round stepwise rounds; Online Resource 2 of the manuscript; the author-confirmed v7 increment. Run `python verify_release.py` in the extracted `mva_aia_reproducibility_v1.1.0` directory. |
| [v1.0.0](https://github.com/ANIIAN91/mva-aia-reproducibility/releases/tag/v1.0.0) | 2026-09-26 | Original AIA evidence (primary, StrawDI, peer, full retraining, MinneApple). Described below. |

Use v1.3.0, v1.2.2, v1.2.1, v1.2.0 and v1.1.0 together with v1.0.0. No release implies submission, acceptance or peer review of the manuscript.

## v1.0.0

Download **mva_aia_reproducibility_v1.0.0.zip** from the [v1.0.0 release](https://github.com/ANIIAN91/mva-aia-reproducibility/releases/tag/v1.0.0), extract it, and run `python verify_release.py` inside the extracted `mva_aia_reproducibility` directory.

This repository hosts entry documents. The versioned ZIP contains the complete 412-file release tree, including the source snapshots, configurations, numerical records, manifests and verifier. Cloning the entry documents alone does not download that tree.

# AIA: reproducibility artifacts for an MVA author-review manuscript

Version: v1.0.0 (2026-09-26). The manuscript is being prepared for Machine
Vision and Applications; this release does not imply submission, acceptance,
or final approval by all manuscript authors.

## Recompute all delivered numerical summaries

Use Python 3.8 or newer, with its standard library only:

```bash
python verify_release.py
```

This checks the release hashes, recomputes the primary/StrawDI/peer summaries,
the full-retraining summaries, and all six MinneApple outcomes. It also checks
18,900 recorded paired batches (6,300 execution-path and 12,600 MinneApple).
It requires no images, credentials, packages, network access or GPU.

## Evidence and boundaries

| Comparison | Paired AP difference (mean ± sample SD) | Scope |
|---|---:|---|
| Original AIA − BoxInst, M18K V1 | +1.3644 ± 0.0765 | Development validation; operational acquisition groups |
| AIA − BoxInst, StrawDI | +0.1393 ± 0.4046 | Previously explored validation; 2/3 positive |
| Optimized − newly retrained original AIA | +0.4081 ± 0.5944 | Three new paired runs; not strict equivalence |
| AIA − BoxInst, MinneApple | −0.1973 ± 0.2099 | All three pairs negative; prior Test use disclosed |

MinneApple BoxInst AP is 28.1526 ± 0.2857 and AIA AP is 27.9553 ± 0.1383.
Lower common-support false coverage and NIS did not imply higher AP.
All prescribed seeds, failed equivalence gates and negative outcomes are retained.
NIS and completeness use separate matchers/supports; do not mix their values.
Historical primary size-AP fields used box area; `mask_area_per_seed.csv`
reports the separate true-mask-area audit. Full AP/AP50/AP75 were unchanged.

## Contents

- `primary/`: primary, subgroup, StrawDI, peer and cost evidence.
- `full_retrain/`: original/optimized paired retraining evidence and sources.
- `minneapple/`: frozen protocol, six results, per-instance/edge scores and sources.
- `PROVENANCE.json`: original and released hashes with exact path-redaction mapping.
- `environment_record.json`: recorded environment, not a new installation test.
- `REPRODUCTION.md`: distinction between arithmetic reproduction and GPU reruns.
- `RIGHTS.md` and `licenses/`: scoped rights and upstream notices.

Source images/masks, model checkpoints, full prediction files, unpublished
manuscript/author-review files and credentials are not included. Fetch source
datasets through their providers under their terms. Frozen original artifacts
remain locally archived; copies here replace local paths with `/WORKSPACE` or
`/LOCAL_HOME`, so their historical embedded hashes describe the originals.
Use `MANIFEST.json` to verify the public bytes. GPU reruns require dependency
installation, provider data, weights, path relocation and fresh engineering
checks; this release does not claim a turnkey or newly reproduced GPU run.

The official MinneApple Test partition had already supported 12 evaluations
in a separate project. Original M18K held-out images were not accessed in the
present extensions. Fresh apple-domain training is not mushroom zero-shot
transfer, pristine blind confirmation or proof of acquisition independence.

For citation, use the repository release URL and exact commit recorded by GitHub.
No DOI is assigned or implied. See `CITATION.md`.
