# Claim Boundaries

What we can say, what we cannot say, and the rule that governs it.

---

## Approved language

These terms are safe to use when mapped to a system, a painpoint, and a proof location:

- "maps painpoints to systems"
- "receipt-backed where supported by artifacts"
- "evidence-backed where proof exists"
- "persistent operational memory"
- "buyer-safe claim boundary"
- "tamper-evident where applicable"
- "simulation-grade where applicable"
- "deny-by-default enforcement where specifically proven by the relevant system"
- "hash-chained receipts"
- "Ed25519 signed where implemented"
- "locally verifiable proof bundle"
- "PASS/FAIL — no soft verdicts"
- "hardened prototype with executed test suites"
- "evidence-mapped to [specific articles]"
- "self-audited with documented methodology"
- "3,400+ executed passing tests"
- "15 independently testable systems"

---

## Forbidden language

The following terms are **forbidden** unless separately proven by an independent authority and reviewed by legal:

- certified
- compliant
- production-grade
- military-grade
- hardware-grade
- tamper-proof
- zero-trust verified
- independently audited
- guaranteed
- enterprise-ready
- perfect
- unbreakable
- universal
- unhackable
- impossible to bypass
- AV-proof
- fully audited (by external party)

See `systems-architecture/FORBIDDEN_PUBLIC_CLAIMS.md` for the full list with reasoning.

---

## Rule

If a claim is not clearly mapped to:

1. a system,
2. a painpoint,
3. a proof location,
4. and a claim boundary,

**do not use it.**

A claim without all four anchors is not a claim — it is marketing. Marketing without proof is a liability.

---

## How to check a claim

1. Find the system in [SYSTEM_SOLUTION_MAP.md](SYSTEM_SOLUTION_MAP.md)
2. Find the painpoint in [PAINPOINT_INDEX.md](PAINPOINT_INDEX.md)
3. Confirm proof exists in `systems-architecture` or the relevant system repo
4. Check the claim boundary in the system file under `systems/`
5. If any of these are missing, the claim is not approved

---

## Source of truth

- `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` — 28 approved claims with evidence
- `systems-architecture/FORBIDDEN_PUBLIC_CLAIMS.md` — 32 forbidden or unsafe claims
- `systems-architecture/CLAIMS_WITH_REQUIRED_QUALIFIERS.md` — claims that need careful wording

---

## Prestige-Forge claim discipline

Prestige-Forge is the claim-safety layer used to keep Razorglint painpoint language honest.

A claim is not ready for buyer-facing use unless it answers:

1. What painpoint does this claim address?
2. Which Razorglint system supports it?
3. Where does the proof live?
4. What wording is buyer-safe?
5. What must we explicitly NOT claim?

If any of these are missing, the claim stays internal or pending.

Every painpoint claim should be treated as Prestige-Forge governed language: mapped to a system, mapped to a proof location, written in buyer-safe wording, and paired with a non-claim boundary.

---

## Self-governance rule

Razorglint public-facing claim maps should be reviewed by Prestige-Forge before publication.

Manual review is useful, but Prestige-Forge verification is the formal claim-safety pass.
