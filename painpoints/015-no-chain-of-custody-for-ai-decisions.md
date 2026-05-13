# No Chain of Custody for AI Decisions

## The pain in one sentence

When AI-assisted decisions affect mission outcomes, there is no cryptographic chain of custody proving what was authorized, by whom, at what authority level, and whether escalation occurred.

## Who feels this pain

- Defense program manager — accountable for mission-critical AI decisions
- Security officer — responsible for access control evidence
- Inspector general — needs chain of custody for investigation
- Contracting officer — must prove decision authority was not exceeded
- Operator — needs to show every step was authorized

## What this pain impacts

- **Legal exposure:** No decision provenance = no defense in post-incident review
- **Mission assurance:** Unclear authorization chain degrades trust in autonomous systems
- **Accountability:** Cannot attribute decisions to specific authority levels
- **Compliance:** NIST 800-53 AU-2/AU-3 describe auditable event records with provenance
- **Procurement risk:** Buyers cannot verify that governance actually constrained AI behavior

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.

## What usually goes wrong

An AI system makes a series of decisions — some autonomous, some escalated to a human. After the fact, no one can prove which decisions were autonomous and which had human authorization. Logs exist but they are mutable, unsigned, and lack authority-level attribution. When an investigation begins, the audit trail cannot distinguish between a properly authorized decision and one that exceeded the system's authority.

## Which Razorglint systems help

- [SAR Guardian](../systems/001-sar-guardian.md) — signed enforcement receipts with actor and reason codes
- [OpenClaw Governed Agents](../systems/002-openclaw-governed-agents.md) — authority-level gating with dual-write evidence
- [Voidlock](../SUPPORTING_SYSTEMS_MAP.md) — capability-bounded execution with collapse receipts
- [Blackiron](../SUPPORTING_SYSTEMS_MAP.md) — hash chains and Merkle proofs for selective disclosure

## How those systems solve it

SAR Guardian produces Ed25519-signed, SHA-256 hash-chained receipts for every governed decision. Each receipt includes the actor, reason code, and timestamp. OpenClaw adds authority-level gating: forbidden action families are hard-blocked, and the trust reaction engine escalates when trust signals conflict. Voidlock bounds execution within a capability cage that records every action and collapses with a self-verifying receipt. Blackiron provides the underlying chain and Merkle primitives, including standalone inclusion proofs that allow selective disclosure — proving a specific decision occurred without revealing the full chain.

## How someone would use this

1. Route AI decisions through SAR Guardian enforcement
2. Configure OpenClaw action families with explicit authority ceilings
3. Wrap autonomous execution in Voidlock cages with declared capabilities
4. After an incident, extract the receipt chain and Merkle inclusion proofs
5. Present proofs to investigators showing exactly what was authorized and what was denied

## License/tier fit

Professional → Enterprise

## How it saves reputation, data, and money

- **Reputation:** Signed receipt chain replaces "we believe the system was authorized" with cryptographic proof
- **Data:** Tamper-evident chains mean custody records cannot be altered after the fact
- **Money:** Post-incident investigations with chain-of-custody evidence resolve in days, not months of forensic reconstruction

## Buyer-safe claim

"Every governed decision on the covered path produces a signed, hash-chained receipt with actor attribution. Authority escalation is enforced where OpenClaw action families are configured. Selective disclosure via Merkle inclusion proofs allows sharing specific evidence without exposing the full chain."

This claim follows Prestige-Forge discipline: mapped to SAR Guardian + OpenClaw + Voidlock + Blackiron, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove every decision in the system passed through governance. It proves that decisions routed through the governed path have cryptographic chain of custody. Ungoverned paths are not covered. Authority-level enforcement depends on correct configuration of action families and capability grants.

## Simple explanation for a 12-year-old

"Imagine a school where every decision about a student — sending them home, giving detention, calling parents — needs to be written down with who decided it, what authority they had, and what time it happened. Right now many AI systems make decisions with no such record. This system creates a tamper-proof decision log that proves who authorized what."

## Where proof lives

- SAR repo — Ed25519-signed receipt chains, reason code taxonomy
- OpenClaw repo — authority-level gating, dual-write evidence, trust reaction logs
- Voidlock repo — capability cage receipts with collapse verdicts
- Blackiron repo — Merkle inclusion proof generation and verification
