# Agent evaluation record

Historical readings from private baseline ab614b1:

- V1: 120 train records.
- V2: 1,500 train records.
- V3: 2,383 sanitized source-grounded public/synthetic examples; adapters were quarantined after holdout regression.
- Spark-agent v1: 500 train, 100 validation, 100 holdout.
- Spark-agent v2: 3,500 train, 350 validation, frozen 500-case holdout; rejected.
- Archived 24/24 loop: selected score 0.618 versus base 0.5328; pre-restart only.

These are historical, not a current model or deployment claim. Raw corpora, adapters, endpoints, and private inventories remain outside this repository.
