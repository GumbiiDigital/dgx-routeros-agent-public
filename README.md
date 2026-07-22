# DGX RouterOS Agent Public

I built this repository to document an evidence-gated AI assistant pattern for network diagnostics and change planning. The design is JSON-first and deliberately separates discovery, evidence retrieval, gating, planning, confirmation, application, and reporting.

## What I built

The public design centers on a strict pipeline:

discover -> retrieve -> gate -> plan -> confirm -> apply -> report

The agent does not earn write authority by producing a plausible plan. It must satisfy fixed evidence gates, present rollback, and receive explicit confirmation before any apply stage can exist.

## Why it matters

Network automation fails dangerously when it confuses a partial observation with the whole system. A reachable management endpoint does not prove the physical path. A visible link does not prove transport behavior. A workload result does not explain why the lower layers are healthy.

I designed the agent to preserve those distinctions.

## Engineering approach

The fixed evidence gates are:

- management_reachability
- physical_link
- l2_l3_topology
- rdma_transport
- nccl
- workload

Each gate records evidence, freshness, result, and reason. A failed or unknown gate blocks dependent actions. Plans include expected effect, rollback, verification, and a confirmation token that is not reusable.

A privacy lint runs before reports are considered publishable.

## Synthetic public-safe architecture

The architecture shows the evidence pipeline with fictional endpoints and documentation-only addresses.

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## Representative work and artifacts

- [Case study](docs/CASE-STUDY.md) - why confirm-to-apply and fixed gates matter.
- [Synthetic change plan](examples/synthetic-change-plan.json) - a JSON-first plan with all required gates.
- [Publication safety](docs/PUBLICATION-SAFETY.md) - privacy and reporting rules.
- [Share copy](docs/SHARE.md) - concise public explanation.
- [Safety checker](scripts/check_publication_safety.py) - repository privacy gate.

## Evidence and lessons

The public evidence is the contract itself: structured gates, explicit refusal logic, rollback fields, synthetic endpoints, JSON validation, and CI privacy checks. The example is not a live change record.

The key lesson is that planning and applying are different capabilities. The assistant can be useful while remaining unable to act.

## Repository map

| Path | Purpose |
|---|---|
| README.md | Agent contract and limits |
| docs/CASE-STUDY.md | Design rationale |
| docs/ARCHITECTURE.md | Synthetic Mermaid pipeline |
| docs/PUBLICATION-SAFETY.md | Public reporting boundary |
| docs/SHARE.md | Share-ready copy |
| examples/ | Synthetic JSON plan |
| scripts/check_publication_safety.py | Privacy and structure checker |
| .github/workflows/publication-safety.yml | CI gate |

## Publication boundary

This is a public project interface, not an operational deployment repository. I publish no live addresses, hostnames, hardware identities, account details, local paths, credentials, raw telemetry, service inventories, private topology, equipment maps, controller identities, or commands targeting real systems. Examples are synthetic and do not reproduce a live environment.

## Limitations

This repository documents a safety architecture, not a deployed agent. It does not claim successful changes, live network access, product endorsement, or operational readiness.
