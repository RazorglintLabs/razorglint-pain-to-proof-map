# Painpoint Tier Matrix

Every painpoint mapped to severity, minimum tier, and pilot boundary.

See [TIER_GATING_RULES.md](TIER_GATING_RULES.md) for tier definitions.
See [PILOT_SCOPE_BOUNDARIES.md](PILOT_SCOPE_BOUNDARIES.md) for what each pilot level includes.

---

| PP | Painpoint | Severity | Minimum tier | Recommended pilot package | Do not give away below | Why |
|----|-----------|----------|--------------|---------------------------|------------------------|-----|
| 001 | We cannot prove what the AI did | S1 Critical | Professional | SAR Enforcement Receipt Pilot | Professional | Core governance proof — receipt chain depth is high-value |
| 002 | Denied actions disappear | S1 Critical | Professional | SAR Enforcement Receipt Pilot | Professional | Enforcement evidence is the backbone of trust |
| 003 | Governance is only policy theater | S1 Critical | Professional | SAR Enforcement Receipt Pilot | Professional | Proof-vs-theater distinction is the sale |
| 004 | Operational memory gets lost | S2 High | Starter | Starter Pilot | Starter | Entry-level pain, low integration depth |
| 005 | Runtime failure gets hidden | S1 Critical | Professional | SAR Enforcement Receipt Pilot | Professional | Failure visibility is safety-critical |
| 006 | Buyer cannot verify claims | S1 Critical | Professional | Professional Pilot | Professional | Buyer-verifiable proof is premium value |
| 007 | Benchmark claims are hard to trust | S2 High | Starter / Professional | Starter Pilot | Starter | Benchmark transparency is low-risk to share |
| 008 | Security work is hard to package safely | S2 High | Professional | Professional Pilot | Professional | BountyPipeline depth is paid |
| 009 | Fleet nodes can drift or go rogue | S1 Critical | Operator | FleetSim Trust Plane Pilot | Operator | Simulation-grade fleet trust is high-value |
| 010 | Policy drift can destroy trust | S1 Critical | Professional | Professional Pilot | Professional | Policy integrity verification is governance core |
| 011 | Operators cannot debug the system | S2 High | Starter / Professional | Starter Pilot | Starter | Debuggability is adoption support |
| 012 | Compliance language can create legal risk | S1 Critical | Professional | Professional Pilot | Professional | Claims safety is reputation-critical |
| 013 | A good system still needs a clear buying path | S2 High | Free / Professional | Discovery Call | Free | Sales enablement — naming the pain is free |
| 014 | Technical proof does not automatically sell | S2 High | Free / Professional | Discovery Call | Free | Sales packaging — naming is free, depth is paid |
| 015 | No chain of custody for AI decisions | S1 Critical | Enterprise | Enterprise Pilot | Enterprise | High-assurance custody chain is top-tier value |
| 016 | Autonomous systems can exceed their authority | S1 Critical | Operator / Enterprise | Operator / Enterprise Pilot | Operator | Authority-bounding is defense-relevant high-value |
| 017 | Cannot prove build pipeline was not tampered with | S1 Critical | Professional / Enterprise | Professional Pilot | Professional | Pipeline integrity evidence is paid |
| 018 | Privileged terminal commands leave no proof | S1 Critical | Professional / Enterprise | Professional Pilot | Professional | Command audit is insider-threat-grade value |
| 019 | Distributed nodes cannot prove event ordering | S2 High | Operator | Operator Pilot | Operator | HLC causal ordering is fleet-grade |
| 020 | No proof of time spent on controlled work | S2 High | Professional / Enterprise | Professional Pilot | Professional | Time accounting evidence is contract-grade value |
| 021 | Fleet nodes can be spoofed or impersonated | S1 Critical | Operator / Enterprise | FleetSim Trust Plane Pilot | Operator | Trust-plane attestation modeling is high-value |
| 022 | Policy changes happen without proof of authorization | S1 Critical | Professional / Enterprise | Professional Pilot | Professional | Policy change control is accreditation-support grade |
| 023 | Cannot verify governance in air-gapped environments | S2 High | Enterprise | Enterprise Pilot | Enterprise | Air-gapped verification is defense-specific top-tier |
| 024 | AI governance evidence does not map to regulatory frameworks | S2 High | Enterprise | Enterprise Pilot | Enterprise | Regulatory-readiness mapping is full-stack Enterprise |
| 025 | No post-incident forensic timeline | S1 Critical | Professional / Enterprise | Professional Pilot | Professional | Multi-source forensic timeline is investigation-grade |
| 026 | Delegated authority cannot be proven or bounded | S1 Critical | Operator / Enterprise | Operator Pilot | Operator | Authority attenuation is defense-relevant |

---

## Severity distribution

| Severity | Count | Painpoints |
|----------|-------|------------|
| S1 Critical | 16 | 001, 002, 003, 005, 006, 009, 010, 012, 015, 016, 017, 018, 021, 022, 025, 026 |
| S2 High | 10 | 004, 007, 008, 011, 013, 014, 019, 020, 023, 024 |
| S3 Medium | 0 | — |
| S4 Low | 0 | — |

## Tier distribution

| Minimum tier | Count | Painpoints |
|-------------|-------|------------|
| Free | 2 | 013, 014 |
| Starter | 3 | 004, 007, 011 |
| Professional | 13 | 001, 002, 003, 005, 006, 008, 010, 012, 017, 018, 020, 022, 025 |
| Operator | 5 | 009, 016, 019, 021, 026 |
| Enterprise | 3 | 015, 023, 024 |

Note: Some Professional-minimum painpoints appear in Enterprise pilots due to solution-depth overlap. Minimum tier is the lowest tier where the painpoint is addressed; higher tiers include deeper coverage.

---

## Non-claim boundary

This matrix is an internal pricing/scoping tool. It does not guarantee savings, prevent incidents, or replace commercial negotiation. Tier assignments reflect value density, not technical exclusion — all systems remain independently testable in their own repos.
