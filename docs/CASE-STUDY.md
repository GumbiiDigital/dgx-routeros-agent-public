# Case study: making network authority explicit

## Actual problem

The private agent spans training, retrieval, runtime schemas, mocked drills, and deployment-adjacent checks. The risk was allowing a partial probe or plausible model answer to imply that mutation was safe.

## Source-backed sequence

1. The RouterOS/Spark corpus and JSON-first scaffold were established.
2. Fixed gate order was formalized: management, physical link, L2/L3, RDMA, NCCL, workload.
3. Artifact validation and report semantics were tightened for unknown fields, missing evidence, and stop-on-first-failure.
4. The v1 restart used 500/100/100 train, validation, and holdout rows.
5. The archived 24/24 optimization loop and 0.618 versus 0.5328 result remain pre-restart evidence.
6. V2 used 3,500/350 and a frozen 500-case holdout; the run was rejected and no current adapter is promoted.

## Failed hypotheses

- Management reachability alone is enough: false.
- A mapped link proves RDMA/NCCL/workload readiness: false.
- A model-generated plan is authority: false.
- One aggregate score proves safe promotion: false.

## Bounded checks and gates

Source checks include corpus counts, retrieval refresh/checks, schema/semantic validation, privacy lint, mocked runtime drills, receipt verification, and scope guards. Public acceptance covers only public artifacts; it does not rerun private training.

## Result

The project demonstrates an evidence contract and refusal behavior. The v2 rejection is a result, not an omission. No live RouterOS change is claimed.
