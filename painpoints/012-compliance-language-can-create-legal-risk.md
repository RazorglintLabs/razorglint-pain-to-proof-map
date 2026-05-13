# Compliance Language Can Create Legal Risk

## The pain in one sentence

Saying "we are compliant" or "certified" without proof creates legal liability — and most companies do it without realizing the risk.

## Who feels this pain

- Founder — personally liable for public claims
- Legal team — responsible for defensible language
- Marketing team — wants strong claims but does not understand boundaries
- Buyer — misled by overclaims, then discovers the gap post-purchase

## What this pain impacts

- **Reputation:** Being caught overclaiming is worse than being modest
- **Legal exposure:** "Compliant" without certification is a provably false statement
- **Money:** Legal action from unsupported claims is expensive
- **Buyer confidence:** Sophisticated buyers penalize overclaiming

## What usually goes wrong

A company builds a good governance system. Marketing writes "fully compliant" or "certified" or "enterprise-ready" on the website. No certification exists. No independent audit has been performed. A buyer relies on those claims, discovers the gap, and either walks away or takes legal action. The company's reputation is damaged by something marketing wrote, not by a technology failure.

## Which Razorglint systems help

- Claims Safety Engine (part of [Prestige-Forge](../systems/006-prestige-forge.md)) — per-claim safety verdicts

## How those systems solve it

The Claims Safety Engine evaluates every claim against the evidence. Each claim gets a verdict: SAFE_TO_SAY (evidence supports it), AT_RISK (evidence is weak or missing), or UNKNOWN (no evidence found). Claims without evidence are flagged before publication. This catches overclaims before they become liabilities.

## How someone would use this

1. List all public claims
2. Run through Claims Safety Engine
3. SAFE_TO_SAY claims can be published
4. AT_RISK claims must be narrowed or dropped
5. UNKNOWN claims must not be published until evidence exists

## License/tier fit

- Professional — claims safety engine
- Enterprise — full claim governance

## How it saves reputation, data, and money

- **Reputation:** No overclaims means no embarrassing retractions
- **Data:** Claim-to-proof tracing is auditable
- **Money:** Avoiding one legal action from overclaiming pays for the entire system

## Buyer-safe claim

"Per-claim SAFE_TO_SAY / AT_RISK verdicts prevent overclaiming before publication."

## What this does NOT prove

This does not provide legal advice. It provides a systematic check of claims against evidence. Legal review is still required. The system reduces risk — it does not eliminate it.

## Simple explanation for a 12-year-old

"Imagine telling everyone you got an A on a test, but you actually got a B+. If someone checks, you look like a liar. This system checks every claim you make and tells you: 'You can safely say this' or 'Do not say this — it is not true enough.' It prevents you from accidentally lying."

## Where proof lives

This repo does not store proof. It maps pain to system.

Proof artifacts for this painpoint live in:
- Prestige-Forge repo — Claims Safety Engine (M-018)
- `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` — 28 approved claims
- `systems-architecture/FORBIDDEN_PUBLIC_CLAIMS.md` — 32 forbidden claims

---

## Non-claim boundary

This does not prove certification, compliance, external audit, universal coverage, production deployment, or that all possible paths are governed. It maps the painpoint to systems and proof locations within the documented scope.
