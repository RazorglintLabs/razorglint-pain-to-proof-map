# System Solution Map

Every Razorglint system, what it does, and which pains it solves.

## Primary pilot systems

For pilot conversations, three systems form the core spine:

1. **SAR Guardian** — enforcement / receipt backbone
2. **OpenClaw Governed Agents** — governed AI-agent pilot surface
3. **FleetSim Trust Plane** — simulation-grade fleet/node trust pilot

Prestige-Forge governs the claims around those pilots.
Truthpacks package the proof.

| System | Simple explanation | Main pains solved | How it works | What it protects | Best buyer/user | Tier/license fit |
|--------|-------------------|-------------------|-------------|-----------------|----------------|-----------------|
| [SAR Guardian](systems/001-sar-guardian.md) | Produces signed, hash-chained enforcement receipts for policy decisions. | 001, 002, 005, 011, 015, 018, 021, 022, 025 | Policy evaluation → receipt → hash chain. Every governed ALLOW and DENY on the covered path is recorded with Ed25519 signatures. Fleet/unit registry with per-agent authentication. | Reputation, data, legal exposure | Security team, auditor, operator, defense PM | Professional → Enterprise |
| [OpenClaw Governed Agents](systems/002-openclaw-governed-agents.md) | Runs AI agents under SAR governance so no agent defines its own rules. | 001, 002, 005, 015, 016, 026 | Agents execute under SAR policy with authority-level gating, forbidden action families, and trust reaction. Outputs exportable as Truthpacks. | Trust, safety, data | AI governance team, CTO, defense PM | Professional → Enterprise |
| [Truthpacks](systems/003-truthpacks.md) | Portable proof packages that a buyer can locally verify using hashes, manifests, and instructions. | 003, 006, 013, 014, 020, 023, 024 | Bundle of evidence + proofs + manifest with SHA-256 integrity. Buyer re-verifies locally. Includes verification instructions for air-gapped environments. | Buyer confidence, trust, reputation | Buyer, investor, auditor, compliance officer | Starter → Enterprise |
| [Persistent Operational Memory](systems/004-persistent-operational-memory.md) | Keeps context, decisions, and reasoning across sessions so nothing is lost. | 004, 011 | Embedding-based retrieval over persisted operational context. Sessions build on prior knowledge. | Operational continuity, time, data | Operator, founder, developer team | Starter → Operator |
| [CTLM Engine](systems/005-ctlm-engine.md) | The reasoning and memory engine that powers contextual decisions across systems. | 004, 007, 011 | Retrieval-augmented reasoning with persistent memory, benchmarked with reproducible results. | Data, operational continuity | Operator, developer team | Operator → Enterprise |
| [Prestige-Forge](systems/006-prestige-forge.md) | Turns intent into verifiable proof. Also serves as the claim-safety layer for Razorglint painpoint language. | 003, 005, 006, 008, 012, 017, 020, 023, 024 | Check → evidence → proof → manifest → bundle → receipt lineage. All SHA-256 hashed. stdlib-only Python. Verification evidence for air-gapped and regulatory contexts. | Reputation, trust, buyer confidence | Auditor, buyer, security team, compliance officer | Professional → Enterprise |
| [FleetSim Trust Plane](systems/007-fleetsim-trust-plane.md) | Models trust-plane behavior in simulation with heartbeat monitoring, severity escalation, attestation-based identity, and authority levels A0–A5. | 009, 016, 019, 021, 026 | Heartbeat → distress pulse → severity ladder → reflex receipt → transition record. Attestation-based identity lifecycle. HMAC-SHA256 per-node credential derivation. A4/A5 human-only authority gates. | Safety, operational continuity, fleet trust | Operator, CTO, fleet manager, defense PM | Operator → Enterprise |
| [BountyPipeline Sidecar](systems/008-bountypipeline-sidecar.md) | Packages security research evidence with chain-of-custody for responsible disclosure. | 008 | Evidence collection → hashing → sanitization → report packaging → handoff checklist. | Reputation, legal exposure, money | Security team, founder | Professional → Enterprise |

### Supporting infrastructure

These systems provide cryptographic primitives and policy infrastructure. See [SUPPORTING_SYSTEMS_MAP.md](SUPPORTING_SYSTEMS_MAP.md) for full details on what each proves and does not prove.

| System | Role | Used by |
|--------|------|---------|
| Blackiron | Hash chains, Merkle trees, HLC causal ordering, receipts (Rust) | Cryptographic foundation (PP-015, PP-017, PP-019, PP-021, PP-023, PP-025) |
| Voidlock | Zero-trust execution cage with deny-by-default capabilities and capability attenuation | Execution governance (PP-001, PP-015, PP-016, PP-023, PP-026) |
| IronSeal | Tamper-evident execution governance for AI pipelines with per-task Merkle proofs | Pipeline proof cages (PP-016, PP-017, PP-023) |
| ChessClock | Append-only hash-chained event log with project/actor/machine attribution | Temporal evidence (PP-002, PP-010, PP-019, PP-020, PP-022, PP-025) |
| PolicySourceEngine | SHA-256-verified deterministic policy pack evaluation | Policy integrity (PP-010, PP-022) |
| Command Guardian | Deny-by-default terminal command enforcement with intent classification | Command safety (PP-002, PP-018, PP-025) |
| Claims Safety Engine | Per-claim SAFE_TO_SAY / AT_RISK verdicts | Claim safety (PP-012) |
| EU AI Act Readiness | Article-to-evidence mapping for EU AI Act (6 articles, read-only adapters) | Regulatory mapping (PP-024) |
