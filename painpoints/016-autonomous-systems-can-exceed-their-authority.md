# Autonomous Systems Can Exceed Their Authority

## The pain in one sentence

Autonomous and AI-assisted systems have no enforced ceiling on what actions they can take — delegation of authority is informal, configurable upward, and leaves no cryptographic evidence of constraint.

## Who feels this pain

- Defense program manager — responsible for autonomous system behavior under DoD Directive 3000.09
- Safety officer — must prove human-in-the-loop requirements are enforced
- CTO — liable when autonomous systems exceed intended scope
- Operator — needs confidence the system cannot self-escalate
- Regulator — demands proof of authority constraints

## What this pain impacts

- **Safety:** Unconstrained autonomous action creates real-world harm
- **Legal exposure:** No proof of authority ceiling = no defense when scope is exceeded
- **Trust:** Operators will not deploy autonomous systems they cannot bound
- **Compliance:** DoD Directive 3000.09 requires human judgment for certain actions — no enforcement mechanism means no governance evidence

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.
- **Mission risk:** Authority escalation in autonomous systems can compromise mission objectives

## What usually goes wrong

An autonomous system is deployed with intended limits — "it can observe and suggest, but not act." Those limits exist as configuration or documentation but not as enforced, irrevocable constraints. The system acquires new capabilities through updates, plugins, or runtime logic. No mechanism prevents a software change from granting capabilities the original authorization did not include. When the system acts beyond its intended scope, there is no cryptographic proof that the boundary existed or was breached.

## Which Razorglint systems help

- [Voidlock](../SUPPORTING_SYSTEMS_MAP.md) — deny-by-default capability cage with monotonic budgets and no reopening
- [OpenClaw Governed Agents](../systems/002-openclaw-governed-agents.md) — forbidden action families, role-scoped validation, trust reaction
- [FleetSim Trust Plane](../systems/007-fleetsim-trust-plane.md) — authority levels A0–A5 with human-only gates at A4/A5
- [IronSeal](../SUPPORTING_SYSTEMS_MAP.md) — per-task capability declaration and enforcement in pipelines

## How those systems solve it

Voidlock enforces deny-by-default capabilities with no add method on the budget tracker. Once a void is sealed, its capability set can only shrink (through nesting/attenuation), never grow. When the void collapses, the receipt is permanent — no reopening. FleetSim enforces an authority hierarchy: A0 (observe only) through A5 (govern, human-only). A3 is the autonomous ceiling — A4 and A5 require human authorization. OpenClaw's forbidden action families (`payments.execute`, `policy.mutate`, `identity.rotate`, `host.exec.unbounded`) are hard-blocked regardless of configuration. IronSeal declares per-task capabilities at pipeline definition time and enforces them during execution.

## How someone would use this

1. Define authority ceilings using FleetSim authority levels (A0–A5)
2. Wrap autonomous execution in Voidlock cages with declared capabilities
3. Configure OpenClaw forbidden families for actions that require human authorization
4. Run pipelines through IronSeal with per-task capability declarations
5. After execution, verify the collapse receipt proves no escalation occurred

## License/tier fit

Operator → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "The system cannot exceed A3 authority — here is the cryptographic proof" replaces "we configured it not to"
- **Data:** Capability attenuation means nested delegation only reduces authority — proof is structural, not policy-based
- **Money:** Preventing one unauthorized autonomous action in a defense context helps avoid authority-exceeded incidents on covered paths

## Buyer-safe claim

"Voidlock enforces deny-by-default capabilities with no budget increase pathway. FleetSim authority levels A4 and A5 require human authorization. OpenClaw forbidden action families are hard-blocked. Capability attenuation in nested voids means delegated authority can only decrease."

This claim follows Prestige-Forge discipline: mapped to Voidlock + FleetSim + OpenClaw + IronSeal, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove that all execution paths pass through a capability cage. It proves that execution routed through Voidlock, OpenClaw, or IronSeal is constrained. Authority levels in FleetSim are simulation-grade — they model the enforcement pattern but are not production fleet management systems. Correct configuration of capability grants and authority ceilings is the deployer's responsibility.

## Simple explanation for a 12-year-old

"Imagine giving a robot a locked toolbox with only the tools it needs. The lock can never be opened wider — only made smaller. If the robot tries to use a tool it doesn't have, the attempt is recorded and denied. And once the toolbox is closed, it stays closed forever."

## Where proof lives

- Voidlock repo — capability cage tests, budget monotonicity proofs, collapse receipts
- FleetSim repo — authority level enforcement, A4/A5 human-gate tests
- OpenClaw repo — forbidden family classification, SAR bridge deny evidence
- IronSeal repo — per-task capability declaration and enforcement
