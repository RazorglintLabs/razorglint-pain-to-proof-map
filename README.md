# Razorglint Painpoint Solver

This repo explains which real-world pains the Razorglint stack solves, which system solves each pain, how it helps, and what value it protects.

It is not an evidence warehouse.
It is not a hype deck.
It is a clear map from pain to solution.

**razorglint-painpoint-solver** explains the pain.
**Prestige-Forge** governs the claim.
**systems-architecture** holds the proof.

That is the clean triangle: pain, claim, proof.

---

## What this repo helps answer

- What problem does this solve?
- Who cares?
- What breaks if this pain is ignored?
- Which Razorglint system helps?
- How does that system help?
- What does it protect?
- How would a buyer use it?
- Which tier/license does it belong in?
- How does it save reputation, data, time, or money?

---

## Main maps

- [PAINPOINT_INDEX.md](PAINPOINT_INDEX.md) — all painpoints in one table
- [SYSTEM_SOLUTION_MAP.md](SYSTEM_SOLUTION_MAP.md) — all systems, what they solve, how they work
- [LICENSE_TIER_MAP.md](LICENSE_TIER_MAP.md) — which tier includes what
- [REPUTATION_DATA_MONEY_MAP.md](REPUTATION_DATA_MONEY_MAP.md) — how the stack saves reputation, data, and money
- [HOW_TO_USE_THIS_STACK.md](HOW_TO_USE_THIS_STACK.md) — practical usage paths for different buyers/operators
- [CLAIM_BOUNDARIES.md](CLAIM_BOUNDARIES.md) — what we can and cannot say
- [SUPPORTING_SYSTEMS_MAP.md](SUPPORTING_SYSTEMS_MAP.md) — cryptographic and policy infrastructure
- [PILOT_STACK_MAP.md](PILOT_STACK_MAP.md) — SAR, OpenClaw, and FleetSim pilot packages
- [TIER_GATING_RULES.md](TIER_GATING_RULES.md) — what each tier unlocks
- [PAINPOINT_TIER_MATRIX.md](PAINPOINT_TIER_MATRIX.md) — severity and minimum tier per painpoint
- [PILOT_SCOPE_BOUNDARIES.md](PILOT_SCOPE_BOUNDARIES.md) — what each pilot level includes and excludes
- [PRICING_MODEL.md](PRICING_MODEL.md) — pricing posture (public-safe)
- [COST_OF_NOT_OWNING_MAP.md](COST_OF_NOT_OWNING_MAP.md) — estimated cost exposure from unresolved pains
- [MEMORY_TYPES_MAP.md](MEMORY_TYPES_MAP.md) — proof memory vs operational context memory
- [GLOSSARY_SIMPLE.md](GLOSSARY_SIMPLE.md) — plain-language definitions

---

## Self-use / dogfooding

This repo is intended to be reviewed through Prestige-Forge before public release.

Prestige-Forge is not only described here as a claim-safety layer. Razorglint uses it to govern Razorglint's own public-facing claims.

Current status: see [PRESTIGE_FORGE_VERIFICATION_STATUS.md](PRESTIGE_FORGE_VERIFICATION_STATUS.md).

---

## Claim safety

Painpoint language in this repo follows Prestige-Forge discipline: every useful claim must be mapped to a system, a proof location, a buyer-safe wording, and a non-claim boundary.

This protects buyers from hype and protects Razorglint from overclaiming.

---

## Repo structure

```
painpoints/      — one file per painpoint, plain language
systems/         — one file per system, what it does and how
tiers/           — license tier breakdowns
examples/        — usage examples
templates/       — templates for adding new painpoints/systems
```

---

## Where proof lives

This repo does **not** store benchmark evidence, test results, or raw proof artifacts.

Proof belongs in:
- `systems-architecture` — portfolio-level evidence, benchmark data, dominance scans
- Each system's own repo — test suites, receipts, proof bundles

This repo only **maps** systems to painpoints and references where proof lives.

---

## Repo status

See [REPO_STATUS.md](REPO_STATUS.md) for current state and next steps.
