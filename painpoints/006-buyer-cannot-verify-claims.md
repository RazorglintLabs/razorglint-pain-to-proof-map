# Buyer Cannot Verify Claims

## The pain in one sentence

The vendor says their system is governed, tested, and secure — but the buyer has no way to verify any of it without trusting the vendor's word.

## Who feels this pain

- Buyer — making a purchase decision based on unverifiable claims
- Investor — evaluating a company based on self-reported metrics
- Auditor — receiving evidence they cannot independently check
- CTO — responsible for vendor selection decisions

## What this pain impacts

- **Trust:** Unverifiable claims erode trust
- **Buyer confidence:** Sophisticated buyers walk away from unverifiable vendors
- **Money:** Wrong purchase decisions from unverifiable claims are expensive
- **Reputation:** Buying based on unverified claims creates downstream risk

## What usually goes wrong

A vendor claims "100% test coverage" or "fully governed" or "enterprise-ready." The buyer asks for evidence. The vendor provides screenshots, PDFs, or access to a dashboard the vendor controls. The buyer cannot independently verify anything. They must trust the vendor — which is exactly what they are trying to avoid.

## Which Razorglint systems help

- [Prestige-Forge](../systems/006-prestige-forge.md) — proof engine
- [Truthpacks](../systems/003-truthpacks.md) — portable, self-verifying proof packages
- Claims Safety Engine — per-claim verification

## How those systems solve it

The vendor generates a Truthpack — a portable package of evidence files, proof files, and a manifest listing every file with its SHA-256 hash. The buyer downloads the Truthpack and re-hashes every file. If the hashes match the manifest, the evidence is authentic. The buyer can locally verify using hashes, manifests, and instructions — without accessing the vendor’s systems and without any special software.

## How someone would use this

1. Request a Truthpack from the vendor
2. Download it
3. Re-hash every evidence file (SHA-256)
4. Compare against the manifest
5. Verify proof chain linkage
6. Make a purchase decision based on math, not marketing

## License/tier fit

- Professional — Truthpack generation + verification
- Enterprise — full proof suite + shareable reports

## How it saves reputation, data, and money

- **Reputation:** Buyers who can verify your claims become advocates, not skeptics
- **Data:** Evidence integrity is mathematically verifiable
- **Money:** Shorter due-diligence cycles = faster sales = less wasted evaluation time

## Buyer-safe claim

"Claims map to proof artifacts. Buyer can locally verify using hashes, manifests, and instructions."

This claim follows Prestige-Forge discipline: mapped to Prestige-Forge + Truthpacks, proof in PF repo output, non-claim boundary below.

## What this does NOT prove

This does not prove the system is perfect. It proves the specific claims made are backed by specific evidence that can be independently verified. Unproven claims should not be made — see [CLAIM_BOUNDARIES.md](../CLAIM_BOUNDARIES.md).

## Simple explanation for a 12-year-old

"Imagine buying a used car. The seller says it passed inspection. But you cannot see the inspection report, and the mechanic works for the seller. This system gives you the full inspection report with tamper-evident stamps so you can check it yourself — no need to trust the seller."

## Where proof lives

This repo does not store proof. It maps pain to system.

Proof artifacts for this painpoint live in:
- Prestige-Forge repo — proof bundles (Truthpacks)
- `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` — 28 claims with evidence citations
- Each system repo — test suites (`pytest` or `cargo test`)
