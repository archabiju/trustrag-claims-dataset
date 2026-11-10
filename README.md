# TrustRAG Claims (v1.0.0)

A hand-labelled, claim-level benchmark for evaluating hallucination detection
in retrieval-augmented generation. Each claim is judged against a small set of
source documents: either the source supports it, or it does not.

## Statistics

| | Count |
| --- | --- |
| Questions | 37 |
| Claims | 109 |
| Supported claims | 70 |
| Hallucinated claims | 39 |
| Source documents | 12 |

## Files

| File | Contents |
| --- | --- |
| `data/trustrag_claims_v1.json` | The dataset, grouped by question. |
| `data/trustrag_claims_v1.csv` | The same data, one claim per row. |
| `scripts/build_test_set.py` | Builds the claim set from the source corpus. The corpus is not included in this release, so the script cannot be re-run from this repository alone. |
| `metadata.json` | Machine-readable description of the dataset. |

## Schema

| Field | Meaning |
| --- | --- |
| `question_id` | Question identifier, `Q01` to `Q37`. |
| `question` | The question the claims answer. |
| `relevant_sources` | Source document filenames holding the evidence. |
| `claim_id` | Claim identifier, for example `Q01-C1`. |
| `claim_text` | A single factual claim. |
| `hallucinated` | `true` if the source does not support the claim, `false` if it does. |

## How the labels were made

Labels follow a faithfulness rule. A claim is supported when the source states
it or directly entails it, and hallucinated when it contradicts the source or
adds a detail the source never states. The full rules and a worked example are
in `ANNOTATION_GUIDELINES.md`.

The dataset was labelled by a **single annotator**. There is no second
annotator and no inter-annotator agreement score.

## Limitations

- The set is small: 109 claims. It suits method checks, not large-scale benchmarking.
- A single annotator means the labels reflect one person's judgement.
- Labels are binary, with no grade for partial support.
## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You may share and
adapt the dataset for any purpose if you credit the creator.

## Citation

```
Archa Biju. TrustRAG Claims (v1.0.0): a hand-labelled claim-level benchmark
for hallucination detection in retrieval-augmented generation. 2026.
Licensed under CC BY 4.0.
```

## Version

1.0.0, released 2026-11-10. See `CHANGELOG.md`.
