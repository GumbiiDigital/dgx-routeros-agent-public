# Case Study: Separating Network Reasoning From Network Authority

## Context

An AI assistant can summarize evidence and propose a change long before it is safe to touch a network. I wanted the architecture to make that gap explicit.

## Problem

A single successful probe can create false confidence. If the assistant jumps from that probe to a configuration change, it skips physical state, topology, transport, collective communication, workload evidence, and rollback readiness.

## What I built

The agent contract has distinct stages:

1. discover identifies available synthetic capabilities.
2. retrieve collects evidence without mutation.
3. gate evaluates the fixed evidence set.
4. plan produces a proposed change and rollback.
5. confirm records a human decision.
6. apply remains unavailable until every dependency is satisfied.
7. report records evidence, action, verification, and unknowns.

The public example ends before apply. Its target uses a documentation-only name and address.

## Engineering decisions

- Gate status is one of pass, fail, or unknown.
- Freshness is part of evidence quality.
- A plan cannot silently weaken a failed gate.
- Confirmation is specific to one plan revision.
- Rollback and post-change verification are mandatory plan fields.
- Privacy lint runs before any report can leave the private boundary.

## Representative artifact

The synthetic change plan captures the pipeline, fixed gates, refusal reasons, and confirmation state. It contains no real configuration and no claim of execution.

## Evidence available here

- The JSON plan is syntactically valid.
- Every fixed evidence gate is represented.
- The plan remains synthetic and non-applied.
- The repository checker rejects common private-data patterns.
- CI repeats the same check.

## Lessons

A useful network assistant should be able to say: the evidence is insufficient, the dependency is unknown, or the rollback is not ready. Those are correct outputs, not failures of usefulness.

## Limitations

The public design does not include vendor configuration, device inventory, actual topology, operational thresholds, or a live control path.
