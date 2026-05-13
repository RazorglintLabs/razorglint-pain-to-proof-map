# SAR Guardian

## One-sentence explanation

SAR Guardian provides signed, hash-chained enforcement receipts for every policy decision on its governed path.

## What pain it solves

- PP-001: We cannot prove what the AI did
- PP-002: Denied actions disappear
- PP-005: Runtime failure gets hidden
- PP-011: Operators cannot debug the system

## How it solves the pain

Every governed action on the covered path passes through a policy evaluator. If the policy says “allow,” a receipt is produced. If it says “deny,” a receipt is also produced. Receipts are hash-chained (each receipt includes the hash of the previous one) so you can detect if any receipt was deleted or changed. Receipts are also signed with Ed25519 cryptographic signatures so you can verify who issued them.

The system that approves the operation never runs the operation. Approval and execution are structurally separated.

SAR Guardian default-allow/blocklist gap remains documented. Deny-by-default applies only where specifically proven by the relevant system/lane (e.g., Voidlock).

## What it protects

- **Reputation:** Provable decision trail when things go wrong
- **Data:** Tamper-evident receipt chain — alteration is mathematically detectable
- **Legal/claim safety:** Ed25519 signed receipts with trust registry
- **Operational continuity:** Receipt chains support post-incident debugging

## Who would use it

- Security team — enforcement proof
- Auditor — verifiable decision trail
- Operator — debugging and tracing
- AI governance team — agent action governance

## How to use it

- Run locally as an enforcement layer
- Review receipt chains (`receipt_ledger.jsonl`) after operations
- Verify signatures against the trust registry
- Use receipts as audit evidence
- Feed receipts into Prestige-Forge for proof bundle generation

## License/tier fit

- Professional
- Operator
- Enterprise

## Value created

- **Reputation:** Every governed decision on the covered path is provable. No “trust me” needed.
- **Data:** 58+ receipt entries, hash-linked, Ed25519 signed, append-only
- **Time:** Incident investigation uses receipt replay instead of manual reconstruction
- **Money:** Reduced audit prep cost, faster incident response

## Proof location

Proof artifacts live in the SAR repo (`C:\SAR\`) and in `systems-architecture`.
This file only maps the system to painpoints.

Test evidence: 497 Python tests + 13 Rust tests.
See `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` claims #10–13.

## Claim boundary

**Can say:**
- "SAR enforces policy with fail-closed behavior. Invalid policy = hard stop."
- "The system that approves the operation never runs the operation."
- "SAR receipts are Ed25519 signed and hash-chained."

**Must not say:**
- "SAR is zero-trust verified" — it implements deny-by-default patterns but has not been independently verified against NIST SP 800-207
- "SAR Guardian uses deny-by-default" — Guardian currently uses blocklist (default-allow). Deny-by-default mode is a documented gap.
- "Signed receipts across all systems" — SAR has Ed25519 signing. Other systems vary.
