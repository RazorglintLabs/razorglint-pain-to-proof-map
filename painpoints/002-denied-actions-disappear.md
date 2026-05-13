# Denied Actions Disappear

## The pain in one sentence

When a system denies an action, the denial often leaves no trace — so there is no proof that enforcement actually happened.

## Who feels this pain

- Security team — needs proof that policies are enforced
- Auditor — needs evidence of enforcement actions
- Operator — needs to understand why something was blocked
- Regulator — needs denial evidence for compliance

## What this pain impacts

- **Safety:** If denials are invisible, enforcement cannot be verified
- **Legal exposure:** Cannot prove you stopped something when asked
- **Trust:** Claiming enforcement without denial proof is hollow
- **Operational time:** Debugging "why was this blocked?" without records wastes time

## What usually goes wrong

A policy blocks an unauthorized action. The system moves on. No record is created. Later, when an auditor asks "prove you blocked unauthorized access on March 15th," the only answer is "our policy was configured to block it." That is not proof — that is a claim about configuration.

## Which Razorglint systems help

- [SAR Guardian](../systems/001-sar-guardian.md) — DENY receipts
- Command Guardian — DENY receipts for terminal commands

## How those systems solve it

Both systems produce receipts for DENY decisions, not just ALLOW decisions. A DENY receipt contains: what was requested, what policy evaluated it, what the decision was, when it happened, and the hash of the previous receipt. The receipt is added to the same hash chain as ALLOW receipts. This means denials are first-class evidence — not logs that might exist somewhere, but provable, hash-chained records.

## How someone would use this

1. Attempt an unauthorized action
2. System denies it and produces a DENY receipt
3. Receipt is added to the hash chain
4. Later, query the receipt chain for all DENY entries
5. Present as proof of enforcement to auditors

## License/tier fit

- Starter — basic denial logging
- Professional — hash-chained DENY receipts

## How it saves reputation, data, and money

- **Reputation:** "Here are the 47 unauthorized actions we blocked last month, with receipts" is powerful
- **Data:** Denial records preserved in tamper-evident chain
- **Money:** Faster audit response — receipts are ready, not reconstructed

## Buyer-safe claim

"Every governed DENY decision on the covered path produces a hash-chained receipt alongside ALLOW decisions."

This claim follows Prestige-Forge discipline: mapped to SAR Guardian + Command Guardian, proof in SAR/CG repos, non-claim boundary below.

## What this does NOT prove

This does not prove that all unauthorized actions were caught. It proves that when the system made a DENY decision, that decision was recorded. Unknown attack vectors may exist outside the policy scope.

## Simple explanation for a 12-year-old

"Imagine a security guard at a building. Right now, the guard stops people who are not allowed in, but never writes it down. Later, nobody can prove the guard did their job. This system makes the guard write a receipt every time they say 'no' — and chains each receipt to the last one so nobody can remove one."

## Where proof lives

This repo does not store proof. It maps pain to system.

Proof artifacts for this painpoint live in:
- SAR repo — DENY receipts in receipt chain
- Command Guardian repo — DENY receipts with hash chain
- `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` — claims #10–13
