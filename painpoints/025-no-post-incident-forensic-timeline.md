# No Post-Incident Forensic Timeline

## The pain in one sentence

After a security incident, breach, or operational failure, there is no cryptographically reliable timeline proving what happened, in what order, on which machines, by which actors — forcing investigators to reconstruct events from mutable, unsigned, easily purged logs.

## Who feels this pain

- Incident responder — first on scene, needs a reliable timeline immediately
- Security officer — responsible for forensic evidence integrity
- Inspector general — investigating potential misconduct or negligence
- Legal team — needs admissible evidence of incident sequence
- Commanding officer — must understand what happened before making decisions

## What this pain impacts

- **Investigation speed:** Without a reliable timeline, reconstruction takes weeks instead of hours
- **Evidence integrity:** Mutable logs can be altered by the attacker or the investigated party
- **Investigation support:** Unsigned, mutable logs have weak evidentiary weight
- **Attribution:** Cannot prove which actor performed which action at which time
- **Containment:** Slow timeline reconstruction delays incident containment decisions

## What usually goes wrong

A security incident occurs. The incident response team arrives and begins log collection. They find syslog entries, application logs, shell history, and database audit records. Each log source uses different timestamp formats, different time zones, and none are integrity-protected. The attacker cleared bash history on two systems. Application logs were rotated and partially overwritten. The timeline the team reconstructs is a best-effort narrative, not a provable sequence. Opposing counsel or an internal review board challenges the timeline, and the team cannot prove it.

## Which Razorglint systems help

- [ChessClock](../SUPPORTING_SYSTEMS_MAP.md) — hash-chained temporal event log with actor, machine, and artifact attribution
- [SAR Guardian](../systems/001-sar-guardian.md) — signed enforcement receipts with fail-closed denial records
- [Command Guardian](../SUPPORTING_SYSTEMS_MAP.md) — hash-chained command-level receipts for terminal activity
- [Blackiron](../SUPPORTING_SYSTEMS_MAP.md) — Hybrid Logical Clock for causal ordering across nodes

## How those systems solve it

ChessClock records events in an append-only, SHA-256 hash-chained JSONL log. Every event includes `timestamp`, `actor`, `machine_id`, `project`, `artifact_hash`, and chain linkage. The chain is verifiable — any modification breaks integrity from the tampered point forward. SAR Guardian's enforcement receipts create a parallel signed chain of every governance decision. Command Guardian records every terminal command attempted, allowed, or denied with hash-chained receipts. Blackiron's HLC enables causal ordering across multiple nodes even when wall clocks disagree. Together, these produce a multi-layered forensic timeline: governance decisions (SAR), terminal commands (Command Guardian), work events (ChessClock), and cross-node ordering (Blackiron HLC).

## How someone would use this

1. Run ChessClock, SAR Guardian, and Command Guardian on governed systems
2. After an incident: collect hash-chained logs from all sources
3. Verify chain integrity on each log to confirm no tampering
4. Merge timelines using Blackiron HLC for causal ordering across nodes
5. Cross-reference SAR receipts (what was allowed/denied) with Command Guardian receipts (what commands were executed)
6. Present the multi-source, hash-verified timeline as forensic evidence

## License/tier fit

Professional → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Here is the hash-verified forensic timeline from 4 independent evidence sources" replaces "we checked the logs"
- **Data:** Append-only chains with per-event hashing prevent post-incident evidence destruction
- **Money:** Reliable forensic timelines reduce investigation duration from weeks to days and strengthen legal position

## Buyer-safe claim

"ChessClock, SAR Guardian, and Command Guardian produce independent, SHA-256 hash-chained event logs with actor and machine attribution. Chain integrity is independently verifiable. Blackiron HLC enables causal event ordering across distributed nodes. Each source is independently tamper-evident."

This claim follows Prestige-Forge discipline: mapped to ChessClock + SAR Guardian + Command Guardian + Blackiron, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove every system event is captured. It proves that events recorded through these systems are tamper-evident and ordered. Attackers who bypass the governed path leave no receipts in these chains — absence of evidence is not evidence of absence. HLC causal ordering requires nodes to participate in the HLC protocol. Log completeness depends on deployment coverage.

## Simple explanation for a 12-year-old

"Imagine 4 security cameras in a building, each recording with a clock that can't be changed. If something bad happens, you can combine the footage from all 4 cameras to see exactly what happened, in what order, and no one can edit the recordings after the fact. That's what these systems do for computer events."

## Where proof lives

- ChessClock repo — hash-chained event log, chain verification, multi-field attribution
- SAR repo — Ed25519-signed enforcement receipt chains
- Command Guardian repo — command-level receipt chains, intent classification
- Blackiron repo — HLC implementation, causal ordering primitives
