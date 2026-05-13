# We Cannot Prove What the AI Did

## The pain in one sentence

When an AI agent does something — good or bad — there is no provable record of what it did, what it was allowed to do, or why it was not stopped.

## Who feels this pain

- CTO — accountable for system behavior
- Security team — responsible for incident investigation
- Auditor — needs decision trail evidence
- Regulator — asks "show me the decision trail"
- Buyer — needs assurance that agent behavior is governed

## What this pain impacts

- **Trust:** No proof = no trust
- **Legal exposure:** Regulator asks for evidence, you have nothing
- **Reputation:** Incident without explanation destroys credibility
- **Safety:** Ungoverned agent actions create real harm
- **Buyer confidence:** Buyers will not adopt unaccountable AI

## What usually goes wrong

An AI agent executes a series of actions. Some are fine. One causes damage. When the team investigates, there is no record of what the agent was authorized to do, what it actually did, or what decisions led to the harmful action. Logs exist but they are mutable — anyone could have changed them after the fact. There is no cryptographic proof that the log is authentic.

## Which Razorglint systems help

- [SAR Guardian](../systems/001-sar-guardian.md) — enforcement receipts for every decision
- [OpenClaw Governed Agents](../systems/002-openclaw-governed-agents.md) — agents under governance
- Voidlock — execution cages with deny-by-default capabilities

## How those systems solve it

Every governed action on the covered path passes through a policy gate. The gate produces a receipt — a signed, hash-chained record of the decision. Allow or deny, the receipt exists. If the agent runs inside a Voidlock execution cage, it also has a capability budget that can only decrease and a chain that can only grow. After the fact, an investigator can replay the receipt chain to see what happened on the governed path, in what order, with what authorization.

SAR Guardian provides signed, hash-chained enforcement receipts. Deny-by-default applies only where specifically proven by the relevant system/lane. SAR Guardian default-allow/blocklist gap remains documented.

## How someone would use this

1. Deploy agents under SAR Guardian governance
2. After an incident, pull the receipt chain
3. Replay the chain to see every decision
4. Verify receipt signatures to confirm authenticity
5. Present the chain as evidence to auditors or regulators

## License/tier fit

- Professional — SAR Guardian enforcement receipts
- Enterprise — full Voidlock execution cages + OpenClaw governed agents

## How it saves reputation, data, and money

- **Reputation:** "Here is the signed decision trail for the governed path" replaces "we think it might have done X"
- **Data:** Tamper-evident chain means receipts on the governed path cannot be silently changed
- **Money:** Incident investigation with receipts takes hours, not weeks

## Buyer-safe claim

"Every governed action on the covered path produces a hash-chained receipt. Actions without explicit capability grants are denied where Voidlock is applied."

This claim follows Prestige-Forge discipline: mapped to SAR Guardian + Voidlock, proof in SAR/Voidlock repos, non-claim boundary below.

## What this does NOT prove

This does not prove the agent made the right decision. It proves the decision was recorded, governed, and verifiable. Good governance does not guarantee good outcomes — it guarantees accountability.

## Simple explanation for a 12-year-old

"Imagine a robot helper at school. Right now, if the robot does something wrong, nobody can prove what happened. This system gives the robot a receipt book — every single thing it does on the watched path gets written down, stamped, and chained to the previous entry. If something goes wrong, you open the book and see exactly what happened."

## Where proof lives

This repo does not store proof. It maps pain to system.

Proof artifacts for this painpoint live in:
- SAR repo — receipt chains, signed enforcement records
- Voidlock repo — execution cage receipts
- OpenClaw repo — dual-write governance records
- `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` — claims #10–16
