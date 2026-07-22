# Publication Safety

## Purpose

I publish the network-assistant safety contract, not a route into a live network.

## Allowed

- Synthetic JSON plans.
- Fictional endpoints and documentation-only addresses.
- Evidence-gate definitions.
- Non-operational rollback and verification concepts.
- Refusal behavior and candid limitations.

## Excluded

- Live configuration, inventory, topology, or service details.
- Accounts, credentials, tokens, device identities, and local paths.
- Raw captures, telemetry, logs, or screenshots.
- Apply instructions aimed at real equipment.
- Claims that a synthetic plan was executed.

## Project-specific review

Every public plan must preserve the discover, retrieve, gate, plan, confirm, apply, and report separation. Apply remains unavailable in synthetic examples. The fixed evidence gates cannot be removed to make a plan look ready.

## Gate

The checker validates JSON, the required evidence-gate names, Mermaid-only architecture, and common private-data patterns. CI runs the same gate. A passing check is not operational approval.
