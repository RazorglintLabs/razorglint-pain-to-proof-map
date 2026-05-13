# Buyer Due Diligence — Example

How a buyer would use this repo to evaluate the Razorglint stack.

---

## Scenario

A CTO at a Series B company is evaluating governance tools for their AI agent platform. They need to answer: "Can we prove what our agents did, to our auditors, with real evidence?"

---

## Step 1: Find the pain

The CTO opens [PAINPOINT_INDEX.md](../PAINPOINT_INDEX.md) and finds:

> PP-001: We cannot prove what the AI did

This matches their problem exactly.

## Step 2: Read the painpoint file

They open [painpoints/001-we-cannot-prove-what-the-ai-did.md](../painpoints/001-we-cannot-prove-what-the-ai-did.md) and learn:
- Who feels this pain (CTO, security team, auditor, regulator)
- What usually goes wrong (mutable logs, no cryptographic proof)
- Which systems help (SAR Guardian, OpenClaw, Voidlock)
- What it does NOT prove (does not guarantee correct decisions — guarantees accountability)

## Step 3: Understand the system

They open [systems/001-sar-guardian.md](../systems/001-sar-guardian.md) and learn:
- SAR produces signed, hash-chained enforcement receipts
- The system that approves the operation never runs the operation
- Claim boundary: SAR Guardian default-allow/blocklist gap remains documented

They also check [SUPPORTING_SYSTEMS_MAP.md](../SUPPORTING_SYSTEMS_MAP.md) for Voidlock:
- Deny-by-default execution cages
- Capabilities attenuate only — children get fewer permissions
- Only governs what is placed inside the void

## Step 4: Check claim boundaries

They open [CLAIM_BOUNDARIES.md](../CLAIM_BOUNDARIES.md) and confirm:
- "tamper-evident" is approved (not "tamper-proof")
- "deny-by-default enforcement" applies where specifically proven
- "certified" and "compliant" are forbidden

## Step 5: Understand the tier

They check [LICENSE_TIER_MAP.md](../LICENSE_TIER_MAP.md):
- Professional tier includes SAR Guardian + Prestige-Forge + Truthpacks
- Enterprise tier adds Voidlock execution cages + OpenClaw governed agents

## Step 6: Ask for proof (elsewhere)

The buyer knows proof is not in this repo. They would request:
- A Truthpack from Prestige-Forge output
- Access to `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` (28 claims with evidence citations)
- Permission to run `pytest` on the relevant system repos

## Step 7: Verify locally

Using the Truthpack:
1. Re-hash every evidence file (SHA-256)
2. Compare against the manifest
3. Verify proof chain linkage
4. Confirm receipt signatures (where Ed25519 is implemented)

No vendor trust required. The math is the verification.

---

## What this example shows

- Pain → system → tier → proof location is a clear path
- Claim boundaries are explicit (what is NOT claimed is as important as what is)
- Proof is not stored in this repo — it is referenced
- The buyer can locally verify using hashes, manifests, and instructions
- Every buyer-safe claim follows Prestige-Forge discipline: mapped to a system, a proof location, buyer-safe wording, and a non-claim boundary

---

## Where proof lives

This example is illustrative. Proof artifacts live in:
- `systems-architecture/` — portfolio evidence
- Each system repo — test suites and receipts
- Prestige-Forge output — Truthpacks and proof bundles

This repo maps pain to system. It does not store proof.
