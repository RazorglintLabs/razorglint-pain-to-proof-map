# Distributed Nodes Cannot Prove Event Ordering

## The pain in one sentence

In distributed systems — fleets, mesh networks, multi-node architectures — events happen across nodes with no shared clock, and there is no causal ordering proof that shows which event happened before, after, or concurrently with another.

## Who feels this pain

- Fleet operator — managing distributed autonomous nodes that report conflicting timelines
- Mission planner — needs to reconstruct what happened across nodes in order
- Incident investigator — must establish causal chains across distributed systems
- System architect — designing multi-domain operations where central time sync is unavailable
- Security analyst — detecting coordinated attacks across distributed nodes

## What this pain impacts

- **Forensics:** Without causal ordering, distributed event reconstruction is unreliable
- **Mission assurance:** Conflicting timestamps across nodes create ambiguity about what happened first
- **Coordination:** Multi-domain operations (JADC2 context) benefit from causal ordering without central coordinators
- **Trust:** Nodes with wall-clock disagreements produce contradictory audit trails
- **Compliance:** Audit trail integrity depends on provable event ordering

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.

## What usually goes wrong

A fleet of nodes — drones, servers, vehicles, edge sensors — operates across a network with unreliable time sync. Node A reports an event at 14:00:01. Node B reports a related event at 14:00:01. Which happened first? Wall clocks disagree. NTP is unreliable in contested or degraded environments. When events need to be reconstructed — for incident response, for mission replay, for audit — the ordering depends on which clock you trust, and no clock has cryptographic authority.

## Which Razorglint systems help

- [Blackiron](../SUPPORTING_SYSTEMS_MAP.md) — Hybrid Logical Clock (HLC) with causal ordering primitives
- [FleetSim Trust Plane](../systems/007-fleetsim-trust-plane.md) — receipt-anchored state transitions across fleet nodes
- [ChessClock](../SUPPORTING_SYSTEMS_MAP.md) — hash-chained temporal event log with actor and machine attribution

## How those systems solve it

Blackiron implements a Hybrid Logical Clock (Kulkarni et al. 2014) in Rust that provides causal ordering across distributed nodes without a central coordinator. Each node maintains an HLC state. `tick()` advances local state. `receive()` merges remote state to establish happens-before relationships. `happens_before()` and `concurrent_with()` determine causal relationships between any two events. Deterministic `tick_at()`/`receive_at()` enable replay. FleetSim anchors every node state transition to a receipt signed by the trust-plane authority. ChessClock adds machine_id + actor + hash-chain linkage for temporal evidence within a single node's timeline.

## How someone would use this

1. Initialize HLC state on each distributed node using Blackiron
2. On local events: `tick()` to advance the clock
3. On inter-node messages: `receive()` to merge causal state
4. After an incident: compare HLC timestamps to establish happens-before ordering
5. Use FleetSim receipts to anchor state transitions with trust-plane authority
6. Use ChessClock for per-node timeline evidence with hash chain integrity

## License/tier fit

Operator → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Here is the causal ordering proof across nodes" replaces "the timestamps were close, we think this happened first"
- **Data:** HLC state merging produces deterministic ordering that survives clock skew and network partitions
- **Money:** Correct event ordering in post-incident analysis helps reduce misattribution and incorrect remediation

## Buyer-safe claim

"Blackiron's Hybrid Logical Clock provides causal event ordering across distributed nodes without a central time coordinator. happens_before() and concurrent_with() are deterministic given the same inputs. FleetSim anchors fleet state transitions to trust-plane-signed receipts."

This claim follows Prestige-Forge discipline: mapped to Blackiron + FleetSim + ChessClock, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove that all nodes use the HLC. Causal ordering is only provable between nodes that participate in the HLC protocol. Nodes that do not call `receive()` on each other's messages have no causal relationship — they are concurrent by definition. FleetSim is simulation-grade. ChessClock is single-node temporal evidence, not distributed consensus.

## Simple explanation for a 12-year-old

"Imagine two friends in different cities texting about what they did today. Their phone clocks are slightly different. If you ask 'who ate lunch first?' you can't tell from the timestamps. This system gives each phone a special clock that tracks not just 'when' but 'what did I know about the other person's events when this happened' — so you can always tell the real order."

## Where proof lives

- Blackiron repo — HLC implementation, causal ordering tests, tick/receive determinism
- FleetSim repo — receipt-anchored transitions, trust-plane authority
- ChessClock repo — hash-chained event log with machine and actor attribution
