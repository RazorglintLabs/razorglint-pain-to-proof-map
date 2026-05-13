# Truthpacks

## One-sentence explanation

Truthpacks are portable proof packages that a buyer can take away and verify without trusting the vendor.

## What pain it solves

- PP-003: Governance is only policy theater
- PP-006: Buyer cannot verify claims
- PP-013: A good system still needs a clear buying path
- PP-014: Technical proof does not automatically sell

## How it solves the pain

A Truthpack bundles evidence files, proof files, a manifest (listing every file with its SHA-256 hash), and verification instructions into a single package. The buyer downloads it, re-hashes every file, checks the manifest, and verifies the proof chain. If anything has been tampered with, the hashes will not match. The buyer can locally verify using hashes, manifests, and instructions — no vendor access required.

## What it protects

- **Buyer confidence:** Local verification using hashes, manifests, and instructions
- **Trust:** Claims are backed by inspectable artifacts
- **Reputation:** Honest packaging builds long-term credibility
- **Money:** Faster due diligence through self-verifying packages

## Who would use it

- Buyer due-diligence team — verify claims before purchase
- Investor — verify portfolio substance
- Auditor — inspect governance evidence
- Security team — review proof integrity

## How to use it

- Receive a Truthpack from the vendor
- Re-hash every evidence file and compare against the manifest
- Verify proof chain linkage (each proof references its evidence hash)
- Check receipt lineage for temporal ordering
- Use verification instructions included in the pack

## License/tier fit

- Starter (read-only verification)
- Professional (full bundle generation)
- Enterprise (full bundle generation + shareable reports)

## Value created

- **Reputation:** Claims are independently verifiable — no "trust me bro"
- **Data:** All evidence is SHA-256 hashed and manifest-checked
- **Time:** Self-verifying packages replace manual evidence gathering
- **Money:** Shorter due-diligence cycles, faster buying decisions

## Proof location

Truthpack generation lives in Prestige-Forge (`C:\prestige-forge\`).
Bundle verification logic is in M-009 Auditor.
See `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` claims #17–19.

## Claim boundary

**Can say:**
- "Buyer can locally verify using hashes, manifests, and instructions"
- "SHA-256 hashed evidence with manifest integrity check"
- "Portable, self-verifying proof package"

**Must not say:**
- "Tamper-proof" — packages are tamper-evident (tampering is detectable), not tamper-proof (tampering is impossible)
- "Certified evidence" — no certification body has reviewed the format
