# DGX RouterOS Agent

I built this as a JSON-first record of a RouterOS-focused agent that separates network reasoning from network authority. The private source baseline is ab614b1 and contains corpus, schemas, runtime code, reports, and training/evaluation receipts.

## What I built

1. Topology-first discovery that does not assume cabling, switch model, hostnames, or node count.
2. Retrieval over source-grounded RouterOS, MikroTik, DGX Spark, NVIDIA, and clean-lab context.
3. Fixed gates: management reachability, physical link, L2/L3 topology, RDMA transport, NCCL, workload.
4. JSON-first topology, gate, plan, apply-receipt, and report artifacts.
5. `confirm_to_apply` authority with rollback and source references; execute remains fail-closed for operator-review plans.
6. Privacy linting, sanitized source paths, and holdout/evaluation records.

## Recorded results

| Observation | Source evidence | Status |
|---|---|---|
| Baseline ab614b1 | private HEAD | Historical |
| Spark-agent v1: 500 train, 100 validation, 100 holdout rows | source README/manifests | Historical |
| Archived loop: 24/24 iterations | source README/receipt verifier | Archived |
| Archived selected score: 0.618 versus base 0.5328 | source README | Historical, not current |
| Spark-agent v2: 3,500 train, 350 validation, frozen 500-case holdout; rejected | source README | Historical decision |
| Contact audit: 193 receipts to training target; no Spark SSH/deploy/doctor contact | source README | Historical audit |

## Why it matters

A reachable management endpoint does not prove physical link, transport, collective communication, or workload health. Fixed ordering makes the first failed dependency visible.

## Engineering approach

Schemas and semantic contracts are checked before artifacts are accepted. Plans require intended changes, rollback, source references, and a confirmation token. Reports retain source hashes and gate order.

## Sanitized architecture boundary

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md). It preserves discovery -> retrieve -> gate -> plan -> confirm -> report without live topology, ports, endpoints, or credentials.

## Repository map

- [docs/CASE-STUDY.md](docs/CASE-STUDY.md)
- [docs/AGENT-EVALUATION-RECORD.md](docs/AGENT-EVALUATION-RECORD.md)
- [docs/PUBLICATION-SAFETY.md](docs/PUBLICATION-SAFETY.md)
- [examples/synthetic-change-plan.json](examples/synthetic-change-plan.json)

## Evidence rules and limits

These are historical source-backed readings, not live status. This is a public project interface, not an operational repository. It publishes no adapters, private inventories, raw corpora, runtime endpoints, or deployment claims.
