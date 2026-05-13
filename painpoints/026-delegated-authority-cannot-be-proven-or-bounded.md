# Delegated Authority Cannot Be Proven or Bounded

## The pain in one sentence

When authority is delegated from a commander to a subordinate to a system, there is no cryptographic proof that each level received less authority than its parent, and no mechanism prevents authority from being escalated or re-granted at a lower level.

## Who feels this pain

- Commanding officer — delegates authority but cannot prove bounds were enforced
- Legal advisor — must show authority chain did not exceed mandate
- Inspector general — investigating whether delegated authority was exceeded
- Program manager — accountable for ensuring autonomous systems operate within delegated bounds
- Operator — needs proof that their actions were within their authorized scope

## What this pain impacts

- **Authority accountability:** Without cryptographic delegation proof, post-incident authority questions are unanswerable
- **Legal exposure:** Exceeding delegated authority creates personal liability in military and government contexts
- **Trust:** Subordinate systems that can self-escalate destroy trust in the delegation chain
- **Mission governance:** Unclear authority boundaries lead to either paralysis (nobody acts) or overreach (everybody acts)
- **Compliance:** Authority delegation must be auditable for IG and congressional oversight

## What usually goes wrong

A commander delegates authority to a subordinate: "You may authorize reconnaissance but not strikes." The subordinate delegates to an AI system: "You may execute reconnaissance tasks." The AI system's configuration file says "reconnaissance" but nothing enforces that ceiling cryptographically. A software update adds a new task type. The AI system executes it because it's in the config. After the fact, no one can prove whether the new task type was within the original delegation or an unauthorized escalation. The authority chain exists as policy documents, not as enforced cryptographic constraints.

## Which Razorglint systems help

- [Voidlock](../SUPPORTING_SYSTEMS_MAP.md) — capability attenuation with nested voids where child ≤ parent
- [FleetSim Trust Plane](../systems/007-fleetsim-trust-plane.md) — authority levels A0–A5 with human-only A4/A5 gates
- [OpenClaw Governed Agents](../systems/002-openclaw-governed-agents.md) — role-scoped validation with forbidden family hard-blocks

## How those systems solve it

Voidlock's nested void architecture enforces mathematical capability attenuation: a child void can only receive a subset of its parent's capabilities, never more. The budget tracker has no add method — resources can only decrease through delegation. Once a void collapses, the receipt proves exactly what capabilities were available and what was consumed. FleetSim's authority levels create an explicit hierarchy: A0 (observe) → A1 (suggest) → A2 (act reversible) → A3 (act governed) → A4 (execute irreversible, human-only) → A5 (govern, human-only). The model proves that A4/A5 actions cannot be delegated to autonomous systems. OpenClaw's role-scoped validation maps agent roles to allowed action family subsets, and forbidden families are hard-blocked regardless of delegation.

## How someone would use this

1. Define authority levels using FleetSim's A0–A5 hierarchy
2. Create the top-level Voidlock cage with full authorized capabilities
3. Nest sub-voids for each delegation level, attenuating capabilities at each step
4. Configure OpenClaw roles with action family subsets matching delegated authority
5. After execution: verify collapse receipts to prove no escalation occurred
6. Present the nested capability chain as proof of bounded delegation

## License/tier fit

Operator → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Here is the nested capability proof showing each delegation level received less authority" replaces "we had a policy about delegation"
- **Data:** Mathematical attenuation (child ≤ parent) is structural — not configurable, not bypassable
- **Money:** Provable bounded delegation helps reduce authority-exceeded incident risk across legal, political, and financial dimensions

## Buyer-safe claim

"Voidlock enforces capability attenuation in nested voids — child capabilities are always a subset of parent capabilities with no escalation pathway. FleetSim authority levels A4/A5 require human authorization. Budget trackers have no increase method. Collapse receipts prove what was available and consumed."

This claim follows Prestige-Forge discipline: mapped to Voidlock + FleetSim + OpenClaw, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove all delegation passes through Voidlock. It proves that delegation modeled through nested voids is mathematically bounded. FleetSim authority levels are simulation-grade. Authority attenuation is structural for Voidlock cages but requires correct initial capability configuration. The model proves the delegation pattern — operational deployment is the deployer's responsibility.

## Simple explanation for a 12-year-old

"Imagine a teacher gives the class president a keyring with 10 keys. The president can give the vice president some keys — but never MORE keys than the president has. The vice president can give the secretary some keys — but never more than the VP has. Each person's keys can only get fewer, never more. And when the job is done, the locks remember exactly which keys were used."

## Where proof lives

- Voidlock repo — nested void capability attenuation tests, budget monotonicity proofs, collapse receipts
- FleetSim repo — authority level hierarchy, A4/A5 human-gate enforcement
- OpenClaw repo — role-scoped validation, forbidden family hard-blocks
