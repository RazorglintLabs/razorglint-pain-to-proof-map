# FleetSim Trust Plane

## One-sentence explanation

FleetSim models trust-plane behavior in simulation using heartbeat monitoring, severity escalation, and transition receipts to detect drift and rogue behavior patterns.

## What pain it solves

- PP-009: Fleet nodes can drift or go rogue

## How it solves the pain

In simulation, every node sends heartbeats. When a node stops responding or behaves outside its expected parameters, a distress pulse is raised. The severity ladder escalates the response (warning → isolation → shutdown signal). Every transition produces a receipt. An operator can see which node drifted, when, what severity was assigned, and what action was signaled — all provable through the receipt chain within simulation scope.

## What it protects

- **Safety:** Drift patterns detected within simulation scope
- **Operational continuity:** Early drift detection models blast radius reduction
- **Trust:** Fleet governance is receipt-backed within simulation scope

## Who would use it

- Operator — fleet management and monitoring
- CTO — fleet governance oversight
- Security team — rogue node detection

## How to use it

- Run FleetSim in simulation mode
- Monitor heartbeat stream within simulation scope
- Review distress pulses and severity transitions
- Inspect transition receipts for governance trail
- Use severity ladder to model escalation thresholds

## License/tier fit

- Operator
- Enterprise

## Value created

- **Reputation:** Governed fleet simulation with receipt trail
- **Data:** Receipt-backed fleet state visibility inside simulation scope
- **Time:** Faster drift pattern identification in simulation
- **Money:** Models blast radius reduction for informed operational decisions

## Proof location

Proof artifacts (simulation-grade) live in the FleetSim repo (`C:\FleetSim\`).
Test evidence: 103 passing tests.
See `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` claims #23–24.

## Claim boundary

**Can say:**
- "FleetSim tests trust-plane enforcement with severity ladder and transition receipts"
- "103 tests passing. Fleet Reflex Loop: heartbeat → distress pulse → reflex receipt."

**Must not say:**
- "Production fleet management" — FleetSim is simulation-grade, not a production fleet manager
- "Prevents all fleet failures" — detects drift and rogue behavior, does not prevent all failure modes
