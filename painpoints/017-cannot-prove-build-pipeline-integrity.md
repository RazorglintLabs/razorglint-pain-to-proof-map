# Cannot Prove Build Pipeline Was Not Tampered With

## The pain in one sentence

Software build and test pipelines produce binaries and reports, but there is no cryptographic proof that each step ran with declared permissions, was not modified mid-execution, and produced the exact outputs claimed.

## Who feels this pain

- Software assurance team — must prove build integrity for accreditation/readiness review
- Security engineer — responsible for supply chain security
- Contracting officer — needs SBOM-adjacent evidence for procurement
- Auditor — asks "prove this binary came from this source through this pipeline"
- Program manager — accountable for software qualification evidence

## What this pain impacts

- **Supply chain trust:** Without pipeline integrity proof, any build artifact is suspect
- **Accreditation support:** NIST 800-218 SSDF and EO 14028 require software supply chain evidence

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.
- **Legal exposure:** Shipping software without build provenance creates liability
- **Buyer confidence:** Sophisticated buyers demand build chain evidence
- **Weapon system qualification support:** MIL-STD-882 / DO-178C verification requires traceable build evidence

## What usually goes wrong

A CI/CD pipeline runs: clone → build → test → package → deploy. Each step produces logs, but those logs are mutable text files with no integrity guarantee. A compromised build agent could alter test results, inject code, or modify outputs between steps. After the fact, there is no way to prove the pipeline ran as declared. Build logs can be edited. Test results can be fabricated. The gap between "we ran tests" and "we can prove we ran tests with these exact permissions and got these exact results" is where supply chain attacks hide.

## Which Razorglint systems help

- [IronSeal](../SUPPORTING_SYSTEMS_MAP.md) — per-task capability enforcement with hash-chained evidence and Merkle proofs
- [Blackiron](../SUPPORTING_SYSTEMS_MAP.md) — domain-separated Merkle trees for standalone inclusion proofs
- [Prestige-Forge](../systems/006-prestige-forge.md) — evidence → proof → manifest → bundle pipeline

## How those systems solve it

IronSeal wraps each pipeline task in a governed execution cage with declared capabilities (`read_fs`, `write_fs`, `execute`, `network`, etc.). Every action is appended to a SHA-256 hash chain. After execution, each task produces a tamper-evident receipt with stdout/stderr hashes, exit code, timing, and chain integrity. A domain-separated Merkle tree covers all task receipts, enabling standalone inclusion proofs — you can prove one specific task's receipt is part of the overall pipeline run without revealing other tasks. Prestige-Forge provides the evidence-to-bundle pipeline for packaging this into inspectable proof artifacts.

## How someone would use this

1. Define pipeline tasks in IronSeal with explicit capability declarations
2. Run the pipeline: each task executes inside its capability cage
3. After completion, collect the bundle: `manifest.json`, `receipts/`, `evidence/`, `chains/`, `merkle.json`, `proofs/`
4. For auditors: extract Merkle inclusion proofs for specific tasks
5. Verification requires only SHA-256 and the documented preimage format — no IronSeal installation needed

## License/tier fit

Professional → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Here is the Merkle inclusion proof for the test step" replaces "trust us, we ran tests"
- **Data:** Hash-chained task receipts mean pipeline evidence cannot be silently altered
- **Money:** Provable build integrity reduces re-testing, re-qualification, and supply chain audit costs

## Buyer-safe claim

"IronSeal wraps each pipeline task in a declared-capability cage and produces per-task SHA-256 hash-chained receipts. Domain-separated Merkle proofs allow offline verification of individual task evidence without IronSeal installation."

This claim follows Prestige-Forge discipline: mapped to IronSeal + Blackiron + Prestige-Forge, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove that all pipelines use IronSeal. It proves that pipelines routed through IronSeal have per-task integrity evidence. It does not prove the source code is correct — it proves the build/test pipeline ran as declared. Pipeline definition is the deployer's responsibility.

## Simple explanation for a 12-year-old

"Imagine building a Lego set where every step — opening the bag, sorting pieces, snapping them together — is photographed, stamped with a time, and chained to the previous photo. If someone claims you skipped a step or used wrong pieces, you can show the chain and prove exactly what happened."

## Where proof lives

- IronSeal repo — pipeline execution receipts, Merkle proofs, bundle output
- Blackiron repo — domain-separated Merkle tree implementation
- Prestige-Forge repo — evidence-to-bundle pipeline
