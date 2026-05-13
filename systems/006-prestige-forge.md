# Prestige-Forge

## One-sentence explanation

Prestige-Forge turns intent into verifiable proof — governed evidence, proofs, manifests, and bundles, all hash-chained and locally verifiable using hashes, manifests, and instructions.

Prestige-Forge is also the **claim-safety layer** for the Razorglint portfolio. Painpoint language across this repo is governed by Prestige-Forge discipline: every claim must be mapped to a system, a proof location, buyer-safe wording, and a non-claim boundary.

## What pain it solves

- PP-003: Governance is only policy theater
- PP-005: Runtime failure gets hidden
- PP-006: Buyer cannot verify claims
- PP-008: Security work is hard to package safely
- PP-012: Compliance language can create legal risk

## How it solves the pain

When you run a check, Prestige-Forge captures the raw output (evidence), computes a deterministic proof (hash of the evidence), adds both to a manifest (inventory of all files with hashes), and assembles everything into a bundle (transportable package). A receipt lineage tracks every step with hash chaining. The result: a buyer or auditor can re-hash every file and verify the entire chain from check to bundle.

The Claims Safety Engine (M-018) checks each claim against the proof. If a claim is not backed by evidence, it gets an AT_RISK verdict. If it is, it gets SAFE_TO_SAY. No soft verdicts.

## What it protects

- **Reputation:** Claims are checked against proof before publication
- **Trust:** Every proof artifact is locally verifiable using hashes and manifests
- **Buyer confidence:** Bundle is self-verifying
- **Legal/claim safety:** AT_RISK claims are flagged before they become liabilities

## Who would use it

- Auditor — verify proof bundles
- Buyer — inspect evidence packs
- Security team — review governance proof
- Founder — ensure claims are safe before publishing

## How to use it

- Run checks through the engine (`pytest` or manual)
- Evidence and proof files are generated automatically
- Build manifest and bundle for distribution
- Run Claims Safety Engine to verify claim safety
- Share Truthpack with buyer or auditor

## License/tier fit

- Professional
- Enterprise

## Value created

- **Reputation:** No overclaims — every claim checked against proof
- **Data:** SHA-256 hashed evidence chain, stdlib-only Python, deterministic
- **Time:** Automated proof generation replaces manual evidence collection
- **Money:** Faster audit prep, reduced legal exposure from overclaims

## Proof location

Proof artifacts live in the Prestige-Forge repo (`C:\prestige-forge\`).
Test evidence: 690 core tests, 15 constitutional families, 19 core modules.
Client Zero: 25/25 PASS, 15/15 SAFE TO SAY.
See `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` claims #17–19.

## Claim boundary

**Can say:**
- "Checks claims against evidence before publication. Unsafe claim = blocked."
- "690 core tests across 15 constitutional families and 19 core modules."
- "stdlib-only Python in the proof path. Reproducible on any machine with Python 3.11+."
- "Prestige-Forge governs the claim language used across painpoint-solver."

**Must not say:**
- "Certified proof engine" — no certification body has reviewed
- "Production-grade" — not independently hardened for production
- "Complete claim coverage" — covers documented claims only

## Role in this repo

Prestige-Forge is named as the claim-safety layer for razorglint-painpoint-solver. Every buyer-safe claim in this repo should be treated as Prestige-Forge governed language: mapped to a system, mapped to a proof location, written in buyer-safe wording, and paired with a non-claim boundary.
