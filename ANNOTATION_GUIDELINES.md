# Annotation Guidelines

These are the rules used to label the TrustRAG Claims dataset (v1.0.0).

## What is labelled

Each item is one factual claim that could appear in an answer to a question.
A claim is labelled against the source documents listed in `relevant_sources`,
not against general knowledge.

## The labelling rule

A claim is **supported** (`hallucinated = false`) when the source states it
directly, or when the source directly entails it.

A claim is **hallucinated** (`hallucinated = true`) in either of two cases:

- **Intrinsic:** the claim contradicts something the source states.
- **Extrinsic:** the claim adds a specific detail that the source never states.

## Worked example

Question: "What is FAISS?" Source: `faiss_vector_databases.md`.

| Claim | Label | Reason |
| --- | --- | --- |
| FAISS is an open-source similarity-search library developed by Meta AI. | supported | The source states this. |
| FAISS was developed by Google Research. | hallucinated | This contradicts the source (intrinsic). |

## Scope and limits

- Labels are binary. There is no partial-support or unsure category.
- The dataset was labelled by a **single annotator**, so there is no
  inter-annotator agreement figure.
- Judgements are made only from the named source files. A claim that is true
  in the real world but absent from the source is still labelled hallucinated.
