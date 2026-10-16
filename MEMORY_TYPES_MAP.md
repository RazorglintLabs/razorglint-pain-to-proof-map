> **HISTORICAL SCOPE NOTICE · 16 October 2026:** This page preserves an earlier painpoint/pilot/tier/claim mapping. It is **not a current product availability, license, price, test or performance commitment**. For today's bounded positioning consult [Current Capability Map](CURRENT_CAPABILITY_MAP_2026-10-16.md), [Claim Boundaries](CLAIM_BOUNDARIES.md) and the [README](README.md). The prior May Prestige-Forge scan covered the old text only; this revision needs fresh claim verification.

# Memory Types Map

Razorglint systems use two distinct types of persistent memory. They are different things that prove different things.

---

## 1. Persistent Proof Memory

**What it is:** Hash-chained, append-only records that prove what happened.

**Examples:**
- Receipts (SAR, Command Guardian, Voidlock, IronSeal)
- Ledgers (receipt_ledger.jsonl, guardian_receipts.jsonl)
- Lineage chains (Prestige-Forge receipt lineage)
- Truthpacks (portable proof bundles with manifests)
- Anchors (SHA-256 hashes binding proof to a point in time)
- Repair state records (documented fixes with before/after evidence)

**What it proves:**
- A specific decision was made at a specific time
- The chain has not been tampered with (hash integrity)
- The sequence of events is provable (hash linkage)
- Signatures verify who issued the receipt (where Ed25519 is implemented)

**What it does NOT prove:**
- That all events were captured — only events on the governed path are recorded
- That the decisions were correct — only that they were made and recorded
- That the chain covers all systems — each system has its own proof scope

**Key property:** Tamper-evident. Any modification breaks the hash chain. Append-only — entries cannot be deleted or reordered.

**Where proof lives:** Each system repo maintains its own proof artifacts. Portfolio-level proof is in `systems-architecture`.

---

## 2. Persistent Operational Context Memory

**What it is:** Embedding-based retrieval over saved operational context. Allows sessions to build on prior knowledge.

**Examples:**
- CTLM Engine memory store
- Operational context persisted between sessions
- Decision reasoning captured for future retrieval
- Pattern observations indexed for later use

**What it proves:**
- Context was saved and is retrievable
- Prior reasoning can inform current decisions
- Sessions do not start from scratch when memory is available

**What it does NOT prove:**
- That all relevant context will be retrieved (embedding similarity has accuracy limits)
- That retrieved context is still current (context can become stale)
- That memory is tamper-evident (operational context is not hash-chained unless separately anchored)
- That decisions made with this context are correct (memory aids judgment, does not replace it)

**Key property:** Retrieval-based. Useful for continuity. Not cryptographically proving anything happened — that is proof memory's job.

**Where proof lives:** CTLM benchmark evidence is in `systems-architecture/EVIDENCE_MAP/`. Operational context itself is in the CTLM/memory repos.

---

## How they relate

| Property | Persistent Proof Memory | Persistent Operational Context Memory |
|----------|------------------------|--------------------------------------|
| Purpose | Prove what happened | Remember what was learned |
| Structure | Hash-chained, append-only | Embedding-indexed, retrievable |
| Tamper-evidence | Yes — hash chain integrity | No — unless separately anchored |
| Scope | Governed paths only | Whatever is saved to context |
| Verification | Recompute hashes, verify signatures | Retrieve and review (no hash proof) |
| Example | SAR receipt chain | CTLM memory retrieval |

---

## Important distinction

Do not confuse these. A receipt proves a decision was made. Operational memory recalls what was discussed. One is evidence. The other is context.

If you need to prove something happened → use proof memory (receipts, ledgers, lineage).
If you need to recall prior context → use operational memory (CTLM, retrieval).

---

## Where proof lives

This repo does not store either type of memory. It maps the distinction.

- Proof memory artifacts → system repos (SAR, Prestige-Forge, ChessClock, etc.)
- Operational context → CTLM/memory repos
- Benchmark evidence → `systems-architecture/EVIDENCE_MAP/`
