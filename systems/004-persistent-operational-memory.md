# Persistent Operational Memory

## One-sentence explanation

Persistent operational memory keeps context, decisions, and reasoning across sessions so operators never start from scratch.

## What pain it solves

- PP-004: Operational memory gets lost
- PP-011: Operators cannot debug the system

## How it solves the pain

Instead of losing everything when a session ends, operational context is stored and indexed using embeddings. When a new session starts, the system retrieves relevant prior context — decisions made, reasoning applied, patterns observed. This means an operator picking up work from yesterday has the context from yesterday, not a blank slate.

## What it protects

- **Operational continuity:** Sessions build on prior knowledge
- **Data:** No context loss between sessions
- **Time:** No rework from forgotten decisions

## Who would use it

- Operator — daily operations with persistent context
- Founder — strategic decisions that build on each other
- Developer team — development context that persists across sprints

## How to use it

- Run the memory service locally
- Context is automatically persisted as operations happen
- Query prior context when needed (embedding-based retrieval)
- Review decision history to understand why past choices were made

## License/tier fit

- Starter (basic)
- Operator (full)

## Value created

- **Reputation:** Consistent decision-making across sessions
- **Data:** Complete operational context preserved
- **Time:** Reduced rework — no re-discovering what was already known
- **Money:** Time saved from not repeating prior work

## Proof location

Proof artifacts live in the CTLM Engine repos and `systems-architecture/EVIDENCE_MAP/`.
Benchmark evidence: `systems-architecture/EVIDENCE_MAP/CTLM_BENCHMARK_EVIDENCE.md`
This file only maps the system to painpoints.

## Claim boundary

**Can say:**
- "Persistent operational memory across sessions"
- "Embedding-based retrieval over operational context"
- "Sessions build on prior knowledge"

**Must not say:**
- "Perfect recall" — retrieval is embedding-based and may not surface all relevant context
- "CTLM reasoning steps are fully auditable" — architecturally true but needs more test evidence before public use
