> **HISTORICAL SCOPE NOTICE · 16 October 2026:** This page preserves an earlier painpoint/pilot/tier/claim mapping. It is **not a current product availability, license, price, test or performance commitment**. For today's bounded positioning consult [Current Capability Map](CURRENT_CAPABILITY_MAP_2026-10-16.md), [Claim Boundaries](CLAIM_BOUNDARIES.md) and the [README](README.md). The prior May Prestige-Forge scan covered the old text only; this revision needs fresh claim verification.

# Supporting Systems Map

These systems provide cryptographic primitives, execution governance, temporal evidence, and regulatory mapping infrastructure used by the primary systems in [SYSTEM_SOLUTION_MAP.md](SYSTEM_SOLUTION_MAP.md).

---

## Voidlock

**What it does:** Zero-trust execution cage. Seals untrusted execution in cryptographically governed voids with deny-by-default capabilities, monotonic budgets, and tamper-evident hash chains.

**How it supports the stack:**
- Provides the deny-by-default execution model for AI agent governance
- Capabilities can only attenuate (children get fewer permissions, never more)
- Budget can only decrease — no escalation pathway
- Every action in the void produces a hash-chained receipt
- Void state is irreversible: once collapsed, it cannot reopen

**Painpoints supported:** PP-001 (AI proof), PP-015 (chain of custody), PP-016 (authority escalation), PP-023 (air-gapped verification), PP-026 (bounded delegation)

**What it proves:** Governed execution within the void produced receipts and respected budgets. Capability attenuation in nested voids is mathematical — child ≤ parent, always.

**What it does NOT prove:** That all execution paths in a system pass through a void. Voidlock governs what is placed inside it — ungovemed paths outside the void are not covered.

**Proof location:** Voidlock repo. 54 tests, stdlib-only Python.

---

## Command Guardian

**What it does:** Deny-by-default terminal command enforcement with hash-chained audit receipts.

**How it supports the stack:**
- Evaluates terminal commands against a policy before execution
- Produces ALLOW and DENY receipts for every decision
- Receipts are SHA-256 hash-chained (append-only)
- Commands that bypass the enforcement layer are not covered

**Painpoints supported:** PP-002 (denied actions), PP-018 (privileged command audit), PP-025 (forensic timeline)

**What it proves:** Commands evaluated by Command Guardian produced receipts for their decisions. Intent classification distinguishes safe, risky, and always-blocked commands.

**What it does NOT prove:** That Command Guardian intercepts all possible command execution paths on the machine. It governs what passes through it.

**Proof location:** Command Guardian repo. 131 tests.

---

## ChessClock

**What it does:** Append-only hash-chained event log with proof packs and standalone verification.

**How it supports the stack:**
- Provides temporal ordering for governance events
- Events are hash-chained (each event includes hash of the previous)
- Proof packs with MANIFEST.sha256 are independently verifiable
- `verify_log.py` enables offline verification

**Painpoints supported:** PP-002 (temporal evidence), PP-005 (failure visibility), PP-010 (policy drift), PP-019 (event ordering), PP-020 (controlled work time), PP-022 (policy change proof), PP-025 (forensic timeline)

**What it proves:** Events written to ChessClock are ordered, hash-chained, and verifiable.

**What it does NOT prove:** That all events in a system are written to ChessClock. Only events routed to it are governed.

**Proof location:** ChessClock repo. Append-only JSONL, MANIFEST.sha256.

---

## PolicySourceEngine

**What it does:** SHA-256-verified policy pack evaluation. Loads policy documents, verifies integrity against manifest hashes, and produces deterministic evaluation verdicts.

**How it supports the stack:**
- Policy packs are integrity-checked before evaluation
- Any modification to a policy file produces a hash mismatch → DEGRADED/FAILED
- Evaluation endpoint produces deterministic PASS/FAIL/DEGRADED verdicts
- Externally verifiable — anyone with the pack can recompute

**Painpoints supported:** PP-010 (policy drift), PP-022 (policy change authorization)

**What it proves:** The policy pack evaluated matches the approved manifest. Drift is detectable.

**What it does NOT prove:** That the policies are correct or complete. It proves integrity, not quality.

**Proof location:** PolicySourceEngine repo. Deterministic evaluation.

---

## Claims Safety Engine (Prestige-Forge M-018)

**What it does:** Per-claim SAFE_TO_SAY / AT_RISK / UNKNOWN verdicts. Traces every claim to specific proof artifacts.

**How it supports the stack:**
- Evaluates each claim against available proof
- SAFE_TO_SAY: evidence directly supports the claim
- AT_RISK: evidence is weak, missing, or ambiguous
- UNKNOWN: no evidence found for this claim
- Temporal drift detection: flags claims whose evidence may be stale

**Painpoints supported:** PP-012 (compliance language risk)

**What it proves:** Claims evaluated by the engine have been checked against available proof.

**What it does NOT prove:** That all possible claims have been evaluated, or that AT_RISK claims are false. It identifies risk, not certainty.

**Proof location:** Prestige-Forge repo. Client Zero: 25/25 PASS, 15/15 SAFE TO SAY.

---

## EU AI Act Readiness

**What it does:** Article-to-evidence mapping for EU AI Act Articles 9, 11, 12, 13, 14, 15. Read-only evidence compiler consuming sealed outputs from sovereign systems.

**How it supports the stack:**
- Maps evidence to specific EU AI Act articles
- Produces gap register identifying unmapped articles
- One-directional data flow: sovereign → adapter → report → customer
- Never writes back into any source system
- 6 adapters produce NormalizedEvidence objects

**Painpoints supported:** PP-008 (regulatory mapping), PP-024 (AI governance framework alignment)

**What it proves:** Evidence has been mapped to specific articles. Gaps have been identified.

**What it does NOT prove:** Compliance. The system explicitly disclaims certification or compliance status. It provides regulatory-readiness mapping.

**Proof location:** EU AI Act Readiness repo. 194 tests. 6 articles covered.

---

## Blackiron

**What it does:** Cryptographic primitives for governed systems — hash chains, Merkle trees, hybrid logical clocks, tamper-evident receipts. Written in Rust.

**How it supports the stack:**
- Domain-separated Merkle trees (leaf/node prefixes prevent second-preimage attacks)
- Hash chains for append-only ledgers
- Hybrid Logical Clock (Kulkarni et al. 2014) for causal ordering across distributed nodes
- Receipt primitives with documented preimage formats
- Deterministic — same inputs = same outputs
- Rust performance — 100x faster chain verification vs Python hashlib
- Standalone Merkle inclusion proofs for selective disclosure

**Painpoints supported:** Foundation for PP-001, PP-002, PP-015 (selective disclosure), PP-017 (Merkle proofs), PP-019 (causal ordering via HLC), PP-021 (receipt infrastructure), PP-023 (cross-language offline verification), PP-025 (causal ordering)

**What it proves:** Cryptographic integrity of chains and trees built using Blackiron primitives.

**What it does NOT prove:** That systems using Blackiron are correctly integrated. Primitives are sound; integration depends on the consuming system.

**Proof location:** Blackiron repo. 53 Rust tests. Preimage formats documented in DOCTRINE.md.

---

## IronSeal

**What it does:** Tamper-evident execution governance for AI agent pipelines. Wraps task execution in cryptographic proof cages with deny-by-default capabilities, monotonic budgets, and append-only hash chains.

**How it supports the stack:**
- Provides execution cages for pipeline-level governance
- Domain-separated Merkle trees (`ironseal:leaf:` / `ironseal:node:`)
- Self-verifying receipts with documented preimage formats
- Offline verification — no network required

**Painpoints supported:** PP-001 (AI proof), PP-005 (failure visibility), PP-016 (authority enforcement in pipelines), PP-017 (build pipeline integrity), PP-023 (air-gapped verification)

**What it proves:** Pipeline execution governed by IronSeal produced receipts and respected budgets.

**What it does NOT prove:** That all pipelines use IronSeal. Only pipelines wrapped in IronSeal cages are governed.

**Proof location:** IronSeal repo. 8 test files, stdlib-only Python.
