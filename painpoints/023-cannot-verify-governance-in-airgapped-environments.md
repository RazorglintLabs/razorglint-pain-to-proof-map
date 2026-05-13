# Cannot Verify Governance in Air-Gapped Environments

## The pain in one sentence

Classified, air-gapped, and disconnected environments cannot verify governance evidence because verification tools depend on network connectivity, cloud services, or external dependencies that are prohibited behind the air gap.

## Who feels this pain

- Classified system administrator — operates in environments with no internet connectivity
- Security officer — must verify governance evidence on isolated networks
- Accreditation reviewer — reviews RMF packages on SIPR/JWICS without external tools
- Deployed operator — field systems have degraded or no network connectivity
- Coalition partner — different tech stacks cannot install verification dependencies

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.

## What this pain impacts

- **Classified operations:** If verification requires network or cloud tools, classified systems cannot verify governance evidence
- **Deployed readiness:** Field-deployed systems in DDIL (denied, disrupted, intermittent, limited) environments lose verification capability
- **Coalition interoperability:** Partners using different operating systems and languages cannot install proprietary verification tools
- **Accreditation support timeline:** Air-gapped evidence verification delays add weeks to ATO processes
- **Trust:** Evidence that cannot be independently verified is not evidence — it is assertion

## What usually goes wrong

A system produces governance evidence — receipts, chains, manifests, proofs. The evidence needs to be verified on a classified network or in a deployed environment. The verification tool requires Python 3.11 with specific packages, or network access to check signatures, or a cloud service for hash verification. None of these are available behind the air gap. The evidence sits unverified because the verification mechanism has external dependencies that are incompatible with the operating environment.

## Which Razorglint systems help

- [Blackiron](../SUPPORTING_SYSTEMS_MAP.md) — Rust primitives with documented preimage formats, no runtime dependency
- [IronSeal](../SUPPORTING_SYSTEMS_MAP.md) — offline verification with documented preimage format, no IronSeal installation needed
- [Voidlock](../SUPPORTING_SYSTEMS_MAP.md) — stdlib-only Python, zero external dependencies
- [Prestige-Forge](../systems/006-prestige-forge.md) — stdlib-only Python proof engine
- [Truthpacks](../systems/003-truthpacks.md) — portable proof bundles with SHA-256 verification instructions

## How those systems solve it

Every cryptographic primitive in the stack uses documented preimage formats. This means verification requires only SHA-256 — available in every language, on every platform, behind every air gap. Blackiron documents its chain preimage as `"{seq}|{timestamp}|{action}|{actor}|{payload_hash}|{prev_hash}"`, its receipt preimage, and its Merkle domain prefixes. IronSeal produces standalone Merkle inclusion proofs verifiable without IronSeal installation. All Python systems (Voidlock, Prestige-Forge, IronSeal) are stdlib-only — zero `pip install` required. Truthpacks include verification instructions inside the bundle so the verifier needs no external documentation.

## How someone would use this

1. Generate evidence and proof bundles on the connected network
2. Transfer bundles to the air-gapped environment (via approved cross-domain solution)
3. On the air-gapped side: verify SHA-256 hashes using any available tool (Python hashlib, OpenSSL, PowerShell, bash)
4. Reconstruct preimages from documented formats and verify chain integrity
5. Check Merkle inclusion proofs using the standalone proof files
6. No installation of Razorglint tools required — only SHA-256

## License/tier fit

Professional → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Verification requires only SHA-256 and the documented preimage format" replaces "install our tool to verify"
- **Data:** Evidence that can be verified behind the air gap is evidence that matters in classified environments
- **Money:** Eliminating air-gap verification delays saves weeks per assessment cycle

## Buyer-safe claim

"All Razorglint cryptographic evidence uses documented preimage formats verifiable with SHA-256 alone. Python core systems are stdlib-only with zero external dependencies. IronSeal Merkle inclusion proofs are standalone — no installation required. Truthpacks include verification instructions inside the bundle."

This claim follows Prestige-Forge discipline: mapped to Blackiron + IronSeal + Voidlock + Prestige-Forge + Truthpacks, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove that SHA-256 alone verifies everything — it verifies hash chains, Merkle proofs, and receipt integrity. Ed25519 signature verification requires Ed25519 support (available in most platforms but not as universal as SHA-256). Cross-domain transfer of evidence bundles is the deployer's responsibility and must follow approved CDS procedures.

## Simple explanation for a 12-year-old

"Imagine you create a locked diary with a secret code. Normally you need a special decoder ring to read it. But this diary uses a code so simple — basic addition and multiplication — that anyone with a calculator can verify it. Even if you're on a desert island with no phone signal, you can still check that nobody changed what was written."

## Where proof lives

- Blackiron repo — documented preimage formats, Rust implementation with minimal deps
- IronSeal repo — standalone Merkle proof files, offline verification tests
- Voidlock repo — stdlib-only implementation, zero dependency verification
- Prestige-Forge repo — stdlib-only proof engine
- Truthpacks — bundle format with embedded verification instructions
