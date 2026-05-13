# Operational Memory Gets Lost

## The pain in one sentence

Every time a session ends, the context, decisions, and reasoning disappear — and the next session starts from scratch.

## Who feels this pain

- Operator — repeats work because context is gone
- Founder — strategic decisions made last week are forgotten
- Developer team — re-discovers the same things across sprints
- Customer — inconsistent experience because the system forgets

## What this pain impacts

- **Operational continuity:** Every session starts from zero
- **Time:** Rework is expensive and demoralizing
- **Data:** Decisions and reasoning are lost permanently
- **Money:** Paying to re-learn what was already known

## What usually goes wrong

An operator works through a complex problem over two days. On day one, they gather context, make decisions, and establish understanding. On day two, they start a new session. All context from day one is gone. They re-discover the same information, re-make the same decisions, and lose hours. Multiply this across a team and across months — the cost is enormous.

## Which Razorglint systems help

- [Persistent Operational Memory](../systems/004-persistent-operational-memory.md) — context that survives sessions
- [CTLM Engine](../systems/005-ctlm-engine.md) — reasoning with persistent memory

## How those systems solve it

Operational context is stored using embeddings and persisted to disk. When a new session starts, the system retrieves relevant prior context automatically. An operator asking a question today gets answers informed by what was learned yesterday, last week, and last month. Decisions build on decisions. Reasoning builds on reasoning.

## How someone would use this

1. Work normally — context is persisted automatically
2. Start a new session — relevant prior context is retrieved
3. Continue where you left off, not from scratch
4. Review decision history when needed

## License/tier fit

- Starter — basic memory
- Operator — full persistent memory with retrieval

## How it saves reputation, data, and money

- **Reputation:** Consistent decisions across time build credibility
- **Data:** No context loss — decisions and reasoning are preserved
- **Money:** Hours saved per week from not re-discovering known information

## Buyer-safe claim

"Operational context persists across sessions with embedding-based retrieval."

## What this does NOT prove

This does not prove the system will always retrieve the most relevant context. Embedding-based retrieval has accuracy limits. It also does not replace human judgment — it provides context for better human decisions.

## Simple explanation for a 12-year-old

"Imagine doing homework and figuring out a hard math method. Then the next day, you forget everything and have to figure it out again. This system is like a notebook that remembers what you learned and shows it to you when you need it again."

## Where proof lives

This repo does not store proof. It maps pain to system.

Proof artifacts for this painpoint live in:
- CTLM/memory repos — operational context stores
- `systems-architecture/EVIDENCE_MAP/` — benchmark evidence
- See [MEMORY_TYPES_MAP.md](../MEMORY_TYPES_MAP.md) for the distinction between proof memory and operational context memory

---

## Non-claim boundary

This does not prove certification, compliance, external audit, universal coverage, production deployment, or that all possible paths are governed. It maps the painpoint to systems and proof locations within the documented scope.
