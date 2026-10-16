> **HISTORICAL SCOPE NOTICE · 16 October 2026:** This page preserves an earlier painpoint/pilot/tier/claim mapping. It is **not a current product availability, license, price, test or performance commitment**. For today's bounded positioning consult [Current Capability Map](CURRENT_CAPABILITY_MAP_2026-10-16.md), [Claim Boundaries](CLAIM_BOUNDARIES.md) and the [README](README.md). The prior May Prestige-Forge scan covered the old text only; this revision needs fresh claim verification.

# Pilot Stack Map

For pilot scope boundaries and tier gating, see [PILOT_SCOPE_BOUNDARIES.md](PILOT_SCOPE_BOUNDARIES.md) and [TIER_GATING_RULES.md](TIER_GATING_RULES.md).

## One-sentence pilot story

"Razorglint pilots show governed AI and trust-plane behavior through receipt-backed decisions, buyer-safe claims, and proof packages."

## Pilot Stack Overview

| Layer | System | Pilot role | What it proves | What it does NOT prove | Best pilot use |
|-------|--------|------------|----------------|------------------------|----------------|
| Enforcement backbone | SAR Guardian | Produces signed/hash-chained enforcement receipts | Covered policy decisions are recorded | Does not prove every possible path is governed | Enforcement receipt pilot |
| Governed agent surface | OpenClaw | Runs AI-agent actions through governance | Covered agent actions can be governed and receipted | Does not prove unrestricted production deployment | AI governance pilot |
| Fleet trust simulation | FleetSim Trust Plane | Models node trust behavior in simulation | Simulated heartbeat/severity/transition logic | Does not prove hardware fleet readiness | Trust-plane simulation pilot |
| Claim safety | Prestige-Forge | Reviews and constrains claims | Claims can be mapped to systems, proof locations, and non-claims | Does not make weak claims true | Buyer-facing claim review |
| Proof delivery | Truthpacks | Packages proof for inspection | Proof can be shared and locally verified | Does not equal external audit | Due diligence package |

## Pilot Package 1 — SAR Enforcement Receipt Pilot

### Buyer pain
"We cannot prove what was allowed, denied, or reviewed."

### Systems used
- SAR Guardian
- Prestige-Forge
- Truthpacks

### What the pilot shows
- A covered decision path produces receipts
- ALLOW and DENY decisions are preserved where routed through the governed path
- Proof can be packaged for review

### What it does NOT show
- Full production deployment
- External audit
- Universal coverage of all execution paths

### Best tier fit
Professional → Enterprise

## Pilot Package 2 — OpenClaw Governed Agent Pilot

### Buyer pain
"We cannot prove what the AI agent did."

### Systems used
- OpenClaw Governed Agents
- SAR Guardian
- Truthpacks
- Prestige-Forge

### What the pilot shows
- Covered AI-agent actions pass through governance
- Decisions are receipted
- Outputs can be packaged into proof
- Buyer-facing claims are constrained by Prestige-Forge discipline

### What it does NOT show
- Certified AI compliance
- Production-grade agent deployment
- Autonomous unrestricted operation

### Best tier fit
Professional → Enterprise

## Pilot Package 3 — FleetSim Trust Plane Pilot

### Buyer pain
"Fleet/node trust can drift silently."

### Systems used
- FleetSim Trust Plane
- SAR Guardian where integrated
- Prestige-Forge
- Truthpacks

### What the pilot shows
- Simulation-grade heartbeat and distress logic
- Severity transitions in a trust-plane model
- Receipt-backed transition evidence inside simulation scope

### What it does NOT show
- Hardware fleet readiness
- Production fleet management
- Military-grade or hardware-grade assurance

### Best tier fit
Operator → Enterprise

## How to talk about pilots safely

Use:
- "pilot"
- "covered path"
- "simulation-grade where applicable"
- "receipt-backed"
- "locally verifiable"
- "buyer-safe claim boundary"

Avoid:
- "production-grade"
- "certified"
- "compliant"
- "hardware-grade"
- "enterprise-ready"
- "guaranteed"
- "all paths"
- "complete coverage"

## Pilot decision guide

| Buyer asks | Lead with |
|------------|-----------|
| Can you prove agent actions? | OpenClaw + SAR |
| Can you prove allow/deny decisions? | SAR Guardian |
| Can you package proof for review? | Truthpacks + Prestige-Forge |
| Can you model node trust drift? | FleetSim Trust Plane |
| Can you keep claims legally safe? | Prestige-Forge |
